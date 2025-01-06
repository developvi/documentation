---
title: "Handling Low Disk Space Conditions"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Handling Low Disk Space Conditions
  parent: 08-tips-techniques-education
  order: 19
---
If you’ve been using your server for a while then, at some point, you MIGHT see a low disk space warning in the HEALTH column of the server list. Here are some tips you can use to reduce the amount of disk space being used.

## Remove Backups

We store a limited number of backups on your server. This makes it faster to restore a recent backup. By default we store 7 days of backups.

You can reduce the number of backups you store as follows:

*   Go to the WpCloudDeploy → CLOUD SERVERS
*   Click on your server to bring up the detail screen
*   Click on the BACKUP tab
*   Scroll down to the PRUNE BACKUPS section
*   Type in a lower number into the RETENTION DAYS field – eg: 3
*   Click the PRUNE BACKUPS FOR ALL SITES ON THIS SERVER button

[![](https://web.archive.org/web/20240420005535im_/https://wpclouddeploy.com/wp-content/uploads/2022/10/wpcd-prune-backups-02.png)](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/wp-content/uploads/2022/10/wpcd-prune-backups-02.png)

This will remove backups older than 3 days from your server.

However, this is a one time task. You can make the change permanent though – see the next section.

## Permanently Reduce The Number Of Backups Kept On Server

You can permanently reduce the number of backups you keep on your server.

To do this, it depends on whether you have enabled server wide backups for all sites (from the SERVER screen) or whether you’ve enabled backups for a site on the SITE screen.

#### If you have enabled server wide backups:

*   Go to the WpCloudDeploy → CLOUD SERVERS
*   Click on your server to bring up the detail screen
*   Click on the BACKUP tab
*   Scroll down to the AUTOMATIC BACKUPS – ALL CURRENT AND FUTURE SITES ON THIS SERVER section
*   If backups are already enabled, disable it
*   Update the RETENTION DAYS field
*   Enable backups again

#### If you have opted to enable backups on a site-by-site basis:

*   Go to the WpCloudDeploy → ALL APPS
*   Click on your site to bring up the detail screen
*   Click on the BACKUP & RESTORE tab
*   Scroll down to the AUTOMATIC BACKUPS – THIS SITE ONLY section
*   If backups are already enabled, disable it
*   Update the RETENTION DAYS field
*   Enable backups again

Don’t forget that, in this case, you will need to do this for all sites on your server.

- - -

## Remove Backups For Sites That No Longer Exist

It is possible that you have backups for sites that no longer exist. For example you might have deleted a site or changed the domain name which can both leave backups orphaned.

In this case you will need to login to the server via ssh and then examine the ~/.wp-backup folder for orphaned backups (or /root/.wp-backup).

[How To Login With SSH](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)

- - -

## Other Tools

In some cases you might have a single site that has extremely large files – maybe old backups that were imported from another location for example. You can find these files:

> [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)

> [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)

- - -

## View Diskspace Usage On A Server

After you have finished cleaning up files, you might want to see how space is being used on your server. You can do this as follows:

*   Go to the WpCloudDeploy → CLOUD SERVERS
*   Click on the server to bring up the detail screen
*   Click on the STATISTICS tab
*   Click on the REFRESH button

- - -

## View Diskspace Used By A Site

You can view the amount of space being used by a site (including backups) as follows:

*   Go to the WpCloudDeploy → ALL APPS
*   Click on a site to bring up the detail screen
*   Click on the STATISTICS tab
*   Click on the RECALCULATE button

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420005535/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
