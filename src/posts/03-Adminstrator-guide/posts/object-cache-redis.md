---
title: "Object Cache Redis"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Object Cache Redis
  parent: 03-Adminstrator-guide
  order: 16
---
## Introduction

An object cache can help speed up database queries by caching the results of those queries in memory. One of the most popular object cache is [MemCached](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/). Support for this is included as part of the core DevelopVIDeploy plugin. An additional object cache option is REDIS which we also support in core (as of DVI 5.6)

[![](https://web.archive.org/web/20240304154127im_/https://wpclouddeployent/uploads/2021/01/wpcd-v4-063.png)](https://web.archive.org/web/20240304154127/https://wpclouddeployent/uploads/2021/01/wpcd-v4-063.png)

## Install Redis On a Server

To enable Redis, the package first needs to be installed at the server level. If you’re running DevelopVIDeploy 5.6 or later, all new servers will have it automatically installed. For older servers you can install it as follows:

*   Go to DevelopVIDeploy → All Cloud Servers
*   Click on the server where you’ll be installing Redis
*   Scroll down to the _REDIS_ section
*   Click the _Install Redis_ button

A popup will appear that will offer periodic feedback as the process progresses. When the process is complete you will get a popup confirmation message and the black ‘terminal” window will show the actions that were taken while attempting to install the package.

Once it’s installed, you can then enable it on a site-by-site basis.

- - -

## Activate Redis For A Site

Once Redis has been installed on a server you can activate it for any site on the server.

1.  Go to DevelopVIDeploy → All Apps
2.  Click on the site where you need to turn on the object cache
3.  Click on the _Cache_ tab
4.  Scroll down to the _REDIS_ section
5.  Click on the toggle switch

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup confirmation message and the page will refresh.

You can view a full log of the operation under the SSH LOG screen.

## Deactivate Redis For A Site

To deactivate Redis on a site:

1.  Go to DevelopVIDeploy → All Apps
2.  Click on the site where you need to turn on the object cache
3.  Click on the _Cache_ tab
4.  Scroll down to the _REDIS_ section
5.  Click on the toggle switch if it’s enabled.

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup confirmation message and the page will refresh.

You can view a full log of the operation under the SSH LOG screen.

- - -

## Removing Redis From a Server

Warning: _Before removing Redis from the server, make sure you deactivate it from all sites on the server._ Otherwise, you’ll see heavy delays when you access your site because WordPress will be attempting to connect to a non-existent Redis server.

To remove it:

*   Go to DevelopVIDeploy → All Cloud Servers
*   Click on the affected server
*   Scroll down to the _REDIS_ section
*   Click on the _UNINSTALL REDIS_ button.

_If this procedure does not work, you can remove it using the command line on the server._

- - -

## REDIS vs MemCached

Amazon AWS has an article that [outlines some of the differences between REDIS and MEMCACHED](https://web.archive.org/web/20240304154127/https://aws.amazon.com/elasticache/redis-vs-memcached). Most of these differences do not matter in WordPress because the REDIS cache plugin doesn’t take advantage of them. MemCached uses a multi-threaded architecture which can be useful on a multi-core VM. But REDIS, in general, is more flexible.

In WordPress, MemCached can only use a max size of 1 MB for an object. Sometimes, WordPress objects in MemCached are larger than 1 MB because the options table is just HUGE. This will cause MemCached to actually SLOW DOWN or TIMEOUT your WP site. Redis is substantially better in theses situations.

Generally, given a choice between REDIS and MEMCACHED, we’ll choose REDIS.

[![](https://web.archive.org/web/20240304154127im_/https://wpclouddeployent/uploads/2021/01/redis-vs-memcached.jpg)](https://web.archive.org/web/20240304154127/https://wpclouddeployent/uploads/2021/01/redis-vs-memcached.jpg)

- - -

## Disable Redis For All New Sites

If you do not want REDIS to be automatically enabled for all your new sites there is an option to make that happen:

*   Go to DevelopVIDeploy → SETTINGS → APP: WORDPRESS – SETTINGS
*   Click on the SITES tab on the left side
*   Under the SITE SETUP OPTIONS section, enable the DISABLE THE REDIS OBJECT CACHE checkbox
*   Scroll down and click the SAVE SETTINGS button.

- - -

## Visual Tweaks

You can apply a label next to the titles on the SERVER and SITES list that show which object cache (Redis or Memcached) is enabled. To turn this on:

*   Go to DevelopVIDeploy → SETTINGS → APP: WORDPRESS – SETTINGS
*   Click on the GENERAL tab on the left side
*   Scroll down to the LABELS section
*   Enable the SHOW THE OBJECT SERVER label checkbox
*   Scroll down and click the SAVE SETTINGS button.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Monit / Healing](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304154127/https://wpclouddeploytation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
