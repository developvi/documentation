---
title: "Local & Remote Statuses On Servers"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Local & Remote Statuses On Servers
  parent: 08-tips-techniques-education
  order: 10
---
When you look at the DVI server list, there is a column called LOCAL STATUS. Under there you’ll usually see two status items for each server along with a link to update the remote state.

What do these items mean and what does the update link do?

[![List of servers with arrow pointing to the local status column.](https://web.archive.org/web/20240529160255im_/https://wpclouddeploy.com/wp-content/uploads/2021/05/wpcd-v4-108.png)](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/wp-content/uploads/2021/05/wpcd-v4-108.png)

The first status, usually “Active”, is the status we THINK the server is in. Most times, it means we think that the server is up and running and everything is hunky dory.

The second status is the actual state the server was in the last time we checked. It’s also usually “Active”.

When a server is first created both statuses are set to “Active”.

However, there are times when the remote status and what our local status shows are different. For example, if you power down the server using the server providers’ dashboard, the local and remote status will be different.

You can make sure that the DVI dashboard reflects this difference by clicking on the UPDATE REMOTE STATE link.

That link will go out to the server providers’ api and check the status of the server. It will then update the DVI status metas to reflect the state of the server at that point in time.

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529160255/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
