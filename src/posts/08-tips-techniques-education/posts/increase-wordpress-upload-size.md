---
title: "Increase WordPress Upload Size"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Increase WordPress Upload Size
  parent: 08-tips-techniques-education
  order: 1
---
Straight out of the box, we’ve set the WP upload size to 25M. But there are cases where you might need to increase that limit.

The process for making this adjustment depends on your version of DVI.

## DVI 4.13 and Later Versions

*   Go to DevelopVIDeploy → Applications and click on site you’re working with.
*   Click on the **TWEAKS** tab
*   Scroll down to the **FILE UPLOAD SIZE** section
*   Change the value in the **SIZE** field
*   Click the **CHANGE** button.

## DVI 4.12 and Earlier

_Friendly Note: If you’re not using DVI 4.16.7 or DVI 5.x, you really need to upgrade._

To increase the WordPress Upload File Size in these earlier versions of DVI, you’ll need to change two options – one in PHP and the other in NGINX.

Changing the PHP option is simple – you can do that right inside the DVI dashboard:

*   Go to DevelopVIDeploy → Applications and click on site you’re working with.
*   Click on the **PHP** tab
*   Under the **ADD OR UPDATE SOME COMMON PHP OPTIONS** section, choose the **UPLOAD\_MAX\_FILESIZE** option.
*   Beneath that is a field where you’ll enter the value. You can enter something like _50M_.
*   Click the **SET THE SELECTED OPTION** button.

The next option you’ll need to change is the NGINX configuration. You need to SSH into the server to do this:

1.  SSH into the server using your favorite ssh client.
2.  Once you’re in, use the NANO editor to open the _/etc/nginx/sites-enabled/yourdomain.com_ file. (Replace ‘yourdomain’ with the actual name of your domain.)
3.  A few lines from the top you’ll see the client\_max\_body\_size entry – change it from 25M to 50M (or whatever you need your new value to be).
4.  Save the file and then run the following command: **service nginx restart**.

After both these changes are completed, you should be able to upload larger files to WordPress.

- - -

See also: [Fixing 413 Request Entity Too Large](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/fixing-error-413-request-entity-too-large/) errors.

### More Topics In Tips, Techniques & Education.

*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420014949/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
