---
title: "Transferring Sites Between Servers"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Transferring Sites Between Servers
  parent: 08-tips-techniques-education
  order: 12
---
DevelopVIDeploy has multiple options for moving sites between servers. They are not all the same – they each serve a different use-case.

## Site Tabs: Copy To Server \[Manual\]

This is the primary way to move sites between two DVI servers. With this method though, you end up with TWO site records. So, after a site is copied, you should either delete the original site from DVI or rename the domain on the copied site.

[Documentation](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)

## Site Tabs: Copy To Server \[Scheduled Daily Sync\]

The COPY TO SERVER tab has an option on it to schedule a copy operation once per day. When you schedule a copy operation, a new site record is NOT created (unless you already did a manual copy).

When you need to use the copied site, you can just point your DNS to the IP of the target server.

If you need to permanently use the copied site on the target server, you can update your existing site record to point to the new server – contact our support folks for help with this process.

## Server Sync

This copies ALL sites on one server to a target server on a regular schedule. We do not make a duplicate site record in DVI so you’ll still continue to only see your existing site record.

[Documentation](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-introduction/)

## Importing Sites

You can import sites to a server by using any backup/restore plugin, just like you would at any other host or WP site. With this process you can import sites from non-wpcd servers.

[More Information](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420004705/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
