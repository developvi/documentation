---
title: "Restoring From AWS S3 Into A New Site or Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Restoring From AWS S3 Into A New Site or Server
  parent: 08-tips-techniques-education
  order: 17
---
There are 7 steps to restoring a backup into a new site or a new server.

1.  Add AWS Credentials To New Server
2.  Create site (if it does not already exist)
3.  Download backups from AWS S3 (or S3 compatible service)
4.  Create backup folder on server (if it does not already exist)
5.  Upload backup files
6.  Refresh backup list
7.  Start restore process
8.  Cleanup

## Preliminary Checks And Warnings

Make sure the site you’re restoring to is running the same webserver as when you backed up! You can’t restore OLS sites into NGINX sites or vice-versa.

## 1\. Add AWS Credentials To New Server

Before you can restore a site to a new server, you need to make sure that you have setup your AWS credentials for it.

The easiest way to do this is on the BACKUP tab for the server. On there you do the following:

*   Under the **AWS S3 CREDENTIALS** section, enter the AWS Access key, secret key etc. and click the **SAVE CREDENTIALS** button. (You can skip this step if you have credentials setup in the GLOBAL settings area.)
*   Under the **AUTOMATIC BACKUPS – ALL CURRENT AND FUTURE SITES** section, click the **SCHEDULE IT** toggle. This will add the credentials to the server. (You can immediately disable it if you want – the goal is to get the credentials added to the server and this step makes that happen.)

## 2\. Create Site

While it might be obvious, we do need to mention that you should have a site already created with the same domain you’re trying to restore.

If your original site no longer exists then just create a new site with the same domain name – it will be overwritten during the restore anyway.

If the site record already exists, point it’s IP address to the new server.

## 3\. Download backups from AWS S3

Download three files from AWS (or your AWS S3 compatible service). For example, if the site you’re restoring has a domain of _ems01.vnxv.com_, the three files that need to be downloaded will be:

ems01.vnxv.com\_2022-07-31-11h25m44s\_db.gz
ems01.vnxv.com\_2022-07-31-11h25m44s\_nginx.tar.gz
ems01.vnxv.com\_2022-07-31-11h25m44s\_fs.tar.gz

Note: the date and time stamps for the three files are the same (or for large files, they’ll be slightly different since each part will be backed up at a different time).

## 4\. Create backup folder on server (if it does not already exist)

Log into server via ssh.

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

## 5\. Upload Backup Files

You can use any sFTP tool to upload the backup files to the folder from step 3 above.

## 6\. Point any existing site records to the new server

If you still have SITE records pointing to the old server, the IP address on it needs to be updated to point to the new server. (We mentioned this in step 1 already but it’s important enough to mention again here.)

## 7\. Refresh Backup List

Use the REFRESH button on the BACKUP tab for the site to let DVI know that there are new backup files.

## 8\. Start Restore

Use the RESTORE button on the BACKUP tab to start the restore process.

[![](https://web.archive.org/web/20240529154753im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-restore-01.png)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-restore-01.png)

## 9\. Checks & Cleanup

If you’re doing the restore into a new server you’ll need to do things like change DNS, remove/update caching and so on.

### More Topics In Admin

*   [Backups With AWS S3](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529154753/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
