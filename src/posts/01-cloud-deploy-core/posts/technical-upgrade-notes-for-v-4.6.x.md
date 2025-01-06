---
title: "Technical Upgrade Notes For V 4.6.x"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Upgrade Notes For V 4.6.x
  parent: 01-cloud-deploy-core
  order: 11
---
## Introduction

Version 4.6.x of DevelopVIDeploy will need to update the configuration of existing servers. This upgrade will need to be done in two parts.

*   Part 1: Upgrade NGINX configurations
*   Part 2: Upgrade CERTBOT to use SNAP images
*   Part 3: Add files for 7G firewall

The majority of the rest of this document will outline how to perform the part 1 upgrade manually for users who cannot use the automatic upgrade routine. Instructions for part 2 and part 3 of the upgrade is at the very bottom.

Please make sure that, after you perform the first part of the upgrade, you continue and perform the second and third parts as well – it will be easy to forget to do the other parts if you perform the first part manually.

- - -

## Part 1: Upgrade NGINX configurations – Automatic Upgrade

Version 4.6.0 of DVI includes updated default configurations for servers and sites. The first part of the upgrade process will modify your existing files so that they match our new default configuration.

For the new default configurations we have added:

*   Browser caching of image and media files
*   Browser caching of js and css files
*   Compression of certain file types before transfer between server and browser (gzip)
*   Larger defaults for number of user connections on the web server
*   Turn on HSTS as a default protocol
*   Some additional multi-threading options for the web server.
*   Using the PHP OPCACHE

You can start the automatic upgrade process under the UPGRADES tab for each affected server.

[![](https://web.archive.org/web/20240420003842im_/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-085.png)](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-085.png)

- - -

## Part 1: Upgrade NGINX configurations – Manual Upgrades

As you can see from the above image, you cannot use the automatic upgrade process if you have already added similar rules to your NGINX configuration files.

### You cannot use the automatic upgrade process if any of the following is true:

1\. If you have manually added or updated any of the following directives to your NGINX configuration files:

worker\_cpu\_affinity
worker\_rlimit\_nofile
pcre\_jit
multi\_accept
worker\_connections
accept\_mutex
use epoll;

reset\_timedout\_connection
keepalive\_timeout
variables\_hash\_max\_size
variables\_hash\_bucket\_size
server\_names\_hash\_bucket\_size
aio threads;

add\_header X-Frame-Options
add\_header X-XSS-Protection
add\_header X-Content-Type-Options
add\_header Referrer-Policy
add\_header X-Download-Options

add\_header Strict-Transport-Security
ssl\_stapling
ssl\_stapling\_verify on;

2\. You also cannot use the automatic upgrade process if you have:

*   Added or modified Gzip Settings
*   Added or modified cache-control settings

If you cannot use the automatic update for your server, you can manually update them as described in the next few sections.

**If you manually update your configurations then you will need to use the DO NOT UPGRADE button in the UPGRADES tab to proceed to the 2nd part of the upgrade process!**

- - -

## New Directives in NGINX.CONF

For servers, we are now adding new directives. You can add these to your existing servers if you wish:

### At the top

worker\_cpu\_affinity auto;
worker\_rlimit\_nofile 100000;
pcre\_jit on;

### In the EVENTS block

Replace the entire block with this:

multi\_accept on;
worker\_connections 50000;
accept\_mutex on;
use epoll;

### In the HTTP block

reset\_timedout\_connection on;
keepalive\_timeout 8;
variables\_hash\_max\_size 4096;
variables\_hash\_bucket\_size 512;
server\_names\_hash\_bucket\_size 128;
aio threads;

All of these items are optional and the absence of them will not affect the normal functioning of your site. If you apply all of these changes, the beginning of your revised nginx.conf file will look similar to the following:

[![](https://web.archive.org/web/20240420003842im_/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-460-nginx-conf-01-1.png)](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-460-nginx-conf-01-1.png)

Note that in the image above we have we’ve added some spacing between the directives as well as added a few comments. That’s merely an aesthetic difference though.

- - -

## Gzip

We created a new file called gzip.conf in /etc/nginx/common/.

This file is now automatically included in all new site level configuration files located in /etc/nginx/sites-enabled.

After running the server upgrade script, you can manually add in the following line to each of the site configurations:

\# Compress certain files with gzip.
include /etc/nginx/common/gzip\[.\]conf;

This is optional and the absence of these items will not affect the normal functioning of your site. But if you do not add them it will prevent you from using the DVI console to reliably adjust certain options related to Gzip and performance.

- - -

## Browser Caching

We created a new file called browsercache.conf in /etc/nginx/common/.

This file is now automatically included in all new site level configuration files located in /etc/nginx/sites-enabled.

After running the server upgrade script, you can manually add in the following line to each of the site configurations:

\# Cache certain filetypes in the browser
include /etc/nginx/common/browsercache\[.\]conf;

This is optional and the absence of these items will not affect the normal functioning of your site. But if you do not add them it will prevent you from using the DVI console to reliably adjust items related to these options.

- - -

We added new default security headers to the site configuration files in /etc/nginx/common/.

In the server block we added:

\# Security Headers
add\_header X-Frame-Options "SAMEORIGIN" always;
add\_header X-XSS-Protection "1; mode=block" always;
add\_header X-Content-Type-Options "nosniff" always;
add\_header Referrer-Policy "no-referrer, strict-origin-when-cross-origin" always;
add\_header X-Download-Options "noopen";
add\_header Strict-Transport-Security "max-age=30000000; includeSubDomains; preload" always;

# OSCP Settings
ssl\_stapling on;
ssl\_stapling\_verify on;

This is optional and the absence of these items will not affect the normal functioning of your site. But if you do not add them it will prevent you from using the DVI console to reliably adjust items related to these options.

- - -

## Final Notes

After making changes to your configuration files, please make sure you restart your PHP and NGINX services:

systemctl restart php5.6-fpm
systemctl restart php7.1-fpm
systemctl restart php7.2-fpm
systemctl restart php7.3-fpm
systemctl restart php7.4-fpm
systemctl restart php8.0-fpm

service NGINX restart

- - -

## Part 2: Upgrade CERTBOT to use SNAP images

After you have completed the first part of the upgrade process you will see a new option under the server UPGRADES tab. Just click the button to upgrade the CERTBOT service to use the new SNAP modules. With this update we’ll be able to support wildcard DNS for Multisite and do so using multiple DNS providers.

[![](https://web.archive.org/web/20240420003842im_/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-086.png)](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-086.png)

- - -

## Part 3: Upgrade For 7G Firewall Files

After you have completed the second part of the upgrade process you will see a new option under the server UPGRADES tab. Just click the button to add the 7G firewall files that we will be using in future versions of DVI.

[![](https://web.archive.org/web/20240420003842im_/https://wpclouddeploy.com/wp-content/uploads/2021/04/wpcd-v4-105.png)](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/wp-content/uploads/2021/04/wpcd-v4-105.png)

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240420003842/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
