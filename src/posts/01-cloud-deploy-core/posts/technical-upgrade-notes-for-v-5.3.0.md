---
title: "Technical Upgrade Notes For V 5.3.0"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Upgrade Notes For V 5.3.0
  parent: 01-cloud-deploy-core
  order: 14
---
## Introduction

In version 5.3.0 of DVI we’ve fixed an issue with OpenLiteSpeed servers. You can manually update the servers if you wish or, you can run the automated updates on the UPGRADES tab for each OLS server.

If you’d like to manually update your OLS servers, you can follow the instructions in the CHANGES FOR OPENLITESPEED SITES & SERVERS section immediately below.

We’ve also updated the code for NGINX servers to match the new file name conventions required by the CACHE ENABLER plugin. There is a separate button on the server UPGRADES tab for each NGINX server to start this upgrade. Or you can manually update the servers if you wish.

If you’d like to manually update your NGINX servers, please see the CHANGES FOR NGINX section below.

Additionally, we have removed Ubuntu 18.04 as a default server option. If you are still using Ubuntu 18.04 or have servers that are still built on 18.04 you will need to enable it – please see the third section below titled **CHANGES FOR ALL SERVERS**.

Finally, the 6G rules have been deprecated. So we’ve added an option to remove them from your servers if you’re not using them. The option is located in the UPGRADES tab for each server. 6G is only supported on NGINX servers so the option will not appear for OLS servers.

- - -

## Changes for OpenLiteSpeed Sites and Servers

As mentioned above, these changes can be automatically applied to your OLS servers by using the options on the UPGRADES tab. If you have manually modified your OLS configuration or simply wish to make the changes yourself, here are the details:

_Note: If you’re upgrading from 4.16 or 4.17 and have never installed 5.x, you should follow the [5.x upgrade instructions](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/) instead. This section does not apply since version 4.x did not support OLS servers._

Edit the following file:

/etc/cron.d/openlitespeed\_htaccess\_scan

e.g. – you can open the file using the NANO editor as follows:

sudo nano /etc/cron.d/openlitespeed\_htaccess\_scan

Locate the line with the following contents:

/usr/local/lsws/admin/cgid

Usually – there’s only one line in the file.

Replace the section of the line that contains this string “/usr/local/lsws/admin/cgid” with this:

/usr/local/lsws/cgid

The full line should read as follows:

\*/3 \* \* \* \* root if ! find /var/www/\*/html/ -maxdepth 2 -type f -newer /usr/local/lsws/cgid -name '.htaccess' -exec false {} +; then systemctl restart lsws; fi

When you have finished your edits, don’t forget to save the file.

- - -

## Changes for NGINX Servers

As mentioned above, these changes can be automatically applied to your NGINX servers by using the options on the UPGRADES tab. If you have manually modified your NGINX configuration or simply wish to make the changes yourself, here are the details:

### Fix for Cache Enabler Plugin

Please apply these changes to each of your existing NGINX servers:

Edit the following file:

/etc/nginx/common/cache\_enabler.conf

e.g. – you can open the file using the NANO editor as follows:

sudo nano /etc/nginx/common/cache\_enabler.conf

Locate the two lines with the following contents:

set $cache\_enabler\_uri '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}index.html';
set $cache\_enabler\_uri2 '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}/index.html';

Replace those lines with this:

set $cache\_enabler\_uri '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}${scheme}-index.html';
set $cache\_enabler\_uri2 '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}/${scheme}-index.html';

Then, locate the two lines with the following contents:

set $cache\_enabler\_uri '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}index-webp.html';
set $cache\_enabler\_uri2 '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}/index-webp.html';

Replace those lines with this:

set $cache\_enabler\_uri '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}${scheme}-index-webp.html';
set $cache\_enabler\_uri2 '${custom\_subdir}/wp-content/cache/cache-enabler/${http\_host}${cache\_uri}/${scheme}-index-webp.html';

Then restart the NGINX server

service nginx restart

The reason for this change is because the caching plugin (Cache Enabler) authors changed the naming scheme of the cache files. Unfortunately they did this without notification to users so it took a while before someone noticed this as an issue. The difference in each of the new lines is just the addition of the **{$scheme}-** variable. With this update your cached pages should be served up even faster!

- - -

## Changes For All Servers

### Callbacks

We have updated the callback script to better handle situations where the apt-get checks might not return expected values.

To use the new script you just need to disable callbacks and re-enable them on all your servers.

If you have a lot of servers, the most efficient way to get this done is to use the **BULK ACTIONS** drop-down in the server list.

### Ubuntu 18.04

Ubuntu 18.04 is no longer an option when creating new servers. If you still have 18.04 servers, you will need to enable the option to use them which you can do in the settings area:

*   Navigate to WpCloudDeploy → Settings → APP: WordPress Settings → General
*   Enable the **ENABLE UBUNTU 18.04 LTS** checkbox
*   Click the **SAVE** button at the bottom of the screen

[![](https://web.archive.org/web/20240529144423im_/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-ubuntu-1804-lts-02.png)](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-ubuntu-1804-lts-02.png)

- - -

## Notes

If any server requires an upgrade, you will see the following notice at the top of the servers list:

[![](https://web.archive.org/web/20240529144423im_/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-upgrades-01.png)](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-upgrades-01.png)

Individual servers needing an upgrade will have a notice in the LOCAL STATUS column of the server list. If you don’t have this column enabled or visible you should enable it until all your servers have been upgraded.

## [![](https://web.archive.org/web/20240529144423im_/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-upgrades-03.png)](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-upgrades-03.png)

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Change Domain on Control Plane Server](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/change-domain-on-control-plane-server/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240529144423/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
