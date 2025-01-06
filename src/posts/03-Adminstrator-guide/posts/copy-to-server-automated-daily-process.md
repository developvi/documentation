---
title: "Copy To Server (Automated Daily Process)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Copy To Server (Automated Daily Process)
  parent: 03-Adminstrator-guide
  order: 42
---
\[This is a beta / fast-ring feature. Feel free to play with it but we know there will be some quirks. This is one of those features that may or may not graduate to a production feature.\]

## Introduction

This feature relates to the [COPY TO SERVER](https://web.archive.org/web/20240304155631/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/) (aka SITE SYNC) feature in the core plugin. With this new daily automated copy, you can setup a server process to execute the COPY TO SERVER function once per day on any site.

## Setup

The option appears in the COPY TO SERVER tab on each site in a section titled DAILY SYNC:

[![](https://web.archive.org/web/20240304155631im_/https://developvideploy.com/wp-content/uploads/2022/04/wpcd-v4-267.png)](https://web.archive.org/web/20240304155631/https://developvideploy.com/wp-content/uploads/2022/04/wpcd-v4-267.png)

All you have to do is select your destination server and then click SCHEDULE.

All the caveats outlined in the docs for the [Copy To Server](https://web.archive.org/web/20240304155631/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/) feature apply to this function as well – so make sure you familiarize yourself with them before using this expanded feature.

## Notes

*   We recommend that you run a manual Copy To Server process first and then switch your site over to the copy to verify that it works. In most cases switching your site to the copy involves a simple DNS change. After you’ve verified the copy works you can then delete the copy from the DVI site list and proceed to setting up the daily site sync process. Note: Deleting the copy is very important after a manual site sync test because you don’t want duplicated domain records running around inside DVI.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Shortcodes](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304155631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
