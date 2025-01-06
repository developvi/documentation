---
title: "Resolving Common Issues With CloudFlare"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Resolving Common Issues With CloudFlare
  parent: 06-Troubleshooting-and-FAQs
  order: 5
---
CloudFlare is a great DNS and PROXY service and is our preferred DNS provider. But, it does require certain settings on each of your domain before SSL can be properly configured on your sites.

## SSL/TLS Need To Be Set To **FULL (STRICT)**

*   Login to Cloudflare and navigate to the SSL/TLS tab
*   Click on the OVERVIEW Tab
*   Make sure the SSL/TLS Encryption Mode is set to FULL (STRICT)

[![](https://web.archive.org/web/20240529160728im_/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-cloudflare-ssl-tls-settings-01.png)](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-cloudflare-ssl-tls-settings-01.png)

## Turn off the “Always Use HTTPS” Option

When your site is first created, it does not have an SSL certificate. So if this option is turned on at CloudFlare it will prevent any attempts to issue an SSL certificate because all validation requests to the site will be redirected to HTTPS – which is not yet configured on the site.

*   Login to Cloudflare and navigate to the SSL/TLS tab
*   Click on the EDGE CERTIFICATES Tab
*   Make sure the ALWAYS USE HTTPS option is turned off

[![](https://web.archive.org/web/20240529160728im_/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-cloudflare-ssl-tls-settings-02.png)](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-cloudflare-ssl-tls-settings-02.png)

## Bot Fight Mode

We recommend that you turn this off. When turned on it’s too aggressive and will prevent a lot of pages from being properly rendered for all but the simplest sites.

## Page Rules

Custom page rules are a common source of issues. If you have them and you’re running into issues, turn them off and see if the issues go away.

## Other

If you continue to have issues, double-check that you have only one “A” or “AAAA” record in your DNS. (It is possible to have multiple of these records that point to different IPs.)

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529160728/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
