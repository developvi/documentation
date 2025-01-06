---
title: "WPCD Cron Jobs"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WPCD Cron Jobs
  parent: 03-Adminstrator-guide
  order: 37
---
## Introduction

DevelopVIDeploy uses a log of background Cron jobs to get things done. If you are not using the [WPCD Better Crons](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/) method to fire our background process then certain WP CRON jobs need to be running every 1 minute or so.

In order for servers and sites to be deployed properly, the WP CRON service needs to be working. In particular, the following THREE cron jobs (cron-hooks) need to be running on the server where the DVI plugin is installed:

*   wpcd\_wordpress\_deferred\_actions\_for\_server
*   wpcd\_wordpress\_deferred\_actions\_for\_apps
*   wpcd\_wordpress\_file\_watcher

When the plugin is first installed, these are probably running. But, over time, if other things are installed on your WordPress site, these processes might not start up or might have been killed.

The easiest way to check that they are installed and running is to install the [WP CRONTROL plugin from wordpress.org](https://web.archive.org/web/20240304150311/https://wordpress.org/plugins/wp-crontrol/). Afterwards, go to the TOOLS → CRON EVENTS screen and in the search box on the upper right of that screen, enter “wpcd”. You should then see the following screen:

[![](https://web.archive.org/web/20240304150311im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-v4-271.png)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-v4-271.png)

Notice that there are six items in the above image but the 3 cron jobs listed earlier above are the most critical when deploying a site. If the three items are NOT shown, you should deactivate and reactivate the DVI plugin.

If all six items in the image above are not shown in your installation then you also consider starting an investigation into a root cause.

- - -

## Additional Cron Jobs for Premium Add-ons

The Power Tools add-on include an additional three cron jobs as well:

*   wpcd\_scan\_scheduled\_apps
*   wpcd\_scan\_scheduled+servers
*   wpcd\_scan\_scheduled\_apps\_automatic\_image

[![](https://web.archive.org/web/20240304150311im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-v4-272.png)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-v4-272.png)

These additional cron jobs are not required when deploying a new site. But, if any are missing you should consider initiating a root-cause investigation (if disabling and re-enabling the plugins do not remedy the issue).

- - -

## Cron Related Email Notifications

As of version 4.16, if we detect that any of these cron jobs are not running you will receive an email. The email is sent once every 8 hours but can be turned off under WpCloudDeploy → SETTINGS → MISC in the **CRON WARNING EMAILS** section.

You might get an occasional email if a blip occurs (eg: during a plugin update or some other transient PHP error or maybe caused by a plugin conflict). But if you continue to receive them on a regular basis then you should definitely start to investigate why they are being disabled.

- - -

## Crons Not Running Often Enough

We recommend that a LINUX CRON be configured to force the WP CRON service to fire at least once per minute. Otherwise, the WP CRON process might not run often enough leaving cron jobs to run late.

If we have installed the core DVI server for you or if you use our pre-built images at DigitalOcean or AWS, LINUX CRONS are already set up to run once per minute.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [Disk Quotas](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304150311/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
