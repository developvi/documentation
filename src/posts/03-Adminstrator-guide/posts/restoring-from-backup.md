---
title: "Restoring From Backup"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Restoring From Backup
  parent: 03-Adminstrator-guide
  order: 2
---
## Verify Backup Files Are On The Server

Before you can restore from backup, the backup files must be present on the server.

You can see which backup files are on the server using the REFRESH button in the backup tab:

*   Go to **DevelopVIDeploy** → **ALL APPS** and click on the site that needs to be restored
*   Click on the **BACKUP & RESTORE** tab
*   Scroll down to the **RESTORES** section
*   Click on the **REFRESH BACKUP LIST** button.

If the backup you’re looking for is not there but is located on the AWS S3 (or compatible) service you will need to move the files onto the server – see the BACKUP FILE LOCATIONS section later below.

## Restore Your Site

Now that you’ve verified that the backup files are present on the server, restoring is simple. You have three restore options:

*   RESTORE SELECTED BACKUP – this restores everything (files, database etc.)
*   RESTORE WEB SERVER CONFIGURATION – only restores the web server configuration files
*   RESTORE WP-CONFIG.PHP FILE – restores only the WordPress wp-config.php file

Select a backup from the drop-down and use one of the restore buttons – most often you’ll use RESTORE SELECTED BACKUP to restore everything.

The restore process should throw output similar to the following:

[![](https://web.archive.org/web/20240304145511im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-restore-01.png)](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-restore-01.png)

- - -

## Backup File Locations

If your backup files are not located on the server, you can upload them using sFTP.

But first, you need to make sure that the backup folders exist for the domain (especially if you’re [restoring to a new server](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)).

Log into server via ssh (sudo or root login)

Check to see if a folder called .wp-backup exists

sudo ls ~/.wp-backup

If not, make one:

sudo mkdir ~/.wp-backup

Then, check to see if a folder with the domain name exists:

sudo ls ~/.wp-backup/yourdomain

If it does not, make one:

sudo mkdir ~/.wp-backup/yourdomain

Note: Replace yourdomain in the commands above with your actual domain. For example, if your actual domain is _ems01.vnxv.com_ then your commands will be:

sudo ls ~/.wp-backup/_ems01.vnxv.com_

sudo mkdir ~/.wp-backup/_ems01.vnxv.com_

Now, you can use any sFTP tool to upload the backup files to the ~/.wp-backup/yourdomain folder.

- - -

## Notes

*   You cannot restore sites between different Web Servers – in other words, if you backed up a site running under NGINX, you cannot restore it into a server using the OpenLiteSpeed webserver.
*   The site will be restored to the server and database name in the wp-config.php file that was part of the backup. This has some implications. For example, if you have switched your database to use a remote database but are now trying to restore a backup taken when the database was a localhost database, the restore will attempt to restore to localhost; and, if successful, your site will now be running on localhost instead of using the remote database server you had been using before the restore!
*   If you need to restore a site to a new server, check out this document: [Restoring from AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/).
*   We’re aware of an OLS issue where the DVI UI might show the incorrect version of PHP after a restore. The issue arises if you restore a site that was running on a version of PHP that is not 8.1. Then, the site is restored using that version but the UI will still show PHP 8.1 The fix is easy – just switch the PHP version in the DVI UI to show the correct version after the restore.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [6G Firewall](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304145511/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
