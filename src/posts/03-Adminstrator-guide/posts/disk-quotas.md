---
title: "Disk Quotas"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Disk Quotas
  parent: 03-Adminstrator-guide
  order: 38
---
You can set disk quotas for a site and control what happens to the site when the quota is exceeded.

You can disk quotas globally or individually for a site.

You can also set a quota for all new sites.

- - -

## Set Disk Quota For a Single Site

*   Go to WpCloudDeploy → WordPress Sites
*   Scroll down to the site you want to work with
*   Click on the TITLE/DOMAIN NAME (usually the first or second column)
*   Look for the QUOTAS & LIMITS metabox on the right hand side of the screen
*   Set the quota in megabytes (eg: 1024)
*   Click the UPDATE button on the upper right of the screen.

- - -

## Set Default Disk Quota For All Sites

If you want all your sites to have the same quota you can do so in the settings area.

*   Go to WpCloudDeploy → Settings
*   Click on the APP:WORDPRESS SETTINGS tab
*   On the left side click on the SITES tab
*   Under the DISK QUOTA section, enter a value for the field labeled QUOTA FOR SITES WITHOUT A QUOTA
*   Click the SAVE SETTINGS button at the bottom of the screen.

This option applies to all sites that do not have a separate quota set – i.e.: any site with a zero quota.

Setting this value to zero will disable it and is the default value for new DVI installations.

- - -

## Set a Disk Quota For All New Sites

You can automatically have a disk quota stamped on each new site.

*   Go to WpCloudDeploy → Settings
*   Click on the APP:WORDPRESS SETTINGS tab
*   On the left side click on the SITES tab
*   Under the DISK QUOTA section, enter a value for the field labeled QUOTA FOR NEW SITES
*   Click the SAVE SETTINGS button at the bottom of the screen.

This option will apply a quota value to all new sites and will be visible in the site’s QUOTAS & LIMITS metabox on the right hand side of the site detail screen.

- - -

## Password Protect Site When Quota is Met or Exceeded

You can password protect a site when the quota has been exceeded as follows:

*   Go to WpCloudDeploy → Settings
*   Click on the APP:WORDPRESS SETTINGS tab
*   On the left side click on the SITES tab
*   Under the DISK QUOTA section, check the box for PASSWORD PROTECT SITE WHEN QUOTA EXCEEDED
*   Click the SAVE SETTINGS button at the bottom of the screen.

Note: Do not use this option in combination with the Disable option covered in the next section below.

- - -

## Disable Sites When Quota is Met or Exceeded

You can disable a site when the quota has been exceeded as follows:

*   Go to WpCloudDeploy → Settings
*   Click on the APP:WORDPRESS SETTINGS tab
*   On the left side click on the SITES tab
*   Under the DISK QUOTA section, check the box for DISABLE SITE WHEN QUOTA EXCEEDED
*   Click the SAVE SETTINGS button at the bottom of the screen.

Note: Do not use this option in combination with the Password Protect option covered in the section immediately above.

- - -

## Apply An Admin Lock When Quota is Met or Exceeded

An admin lock prevents users / customers who have access to the front-end dashboard from making changes there. It does not prevent them from viewing the site or logging into it.

You can apply an admin lock to a site when the quota has been exceeded as follows:

*   Go to WpCloudDeploy → Settings
*   Click on the APP:WORDPRESS SETTINGS tab
*   On the left side click on the SITES tab
*   Under the DISK QUOTA section, check the box for APPLY ADMIN LOCK WHEN QUOTA EXCEEDED
*   Click the SAVE SETTINGS button at the bottom of the screen.

- - -

## Quota Alerts

You can setup alerts when quotas are exceeded under the SERVER ALERTS → PROFILES screen. And you can view recent alerts under SERVER ALERTS → NOTIFICATIONS.

[![](https://web.archive.org/web/20240529153239im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v5-quota-alerts-notifications-01.png)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v5-quota-alerts-notifications-01.png)

Get more information about how to use and configure alerts in our [Alerts Documentation](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/).

- - -

## Disk Quotas & Site Expiration

You can combine Disk Quotas & [Site Expirations](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/) in an interesting way.

You can set a site expiration when a quota is exceeded – example, 30 days. This allows the site to stay up for a period of time after the quota is exceeded. Then, when the expiration date arrives, stricter expiration rules can apply (such as deleting the site or locking it.)

- - -

## Related Articles

*   [Release notes for DVI v 5.0](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/whats-new-in-wpclouddeploy-5-0)

- - -

## Important Notes

*   Quotas are evaluated once a day when callbacks are run and data is pushed from servers to the plugin.
*   If your use case is such that you need regular alerts on disk usage then you should use the alerts functions with MONIT that are available under a server’s HEALING tab.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529153239/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
