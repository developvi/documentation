---
title: "Import Sites"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Import Sites
  parent: 08-tips-techniques-education
  order: 13
---
When you’re looking to move a site from an existing host to one of your new DVI servers, you can usually use any backup and restore plugin. This allows you to import sites from many of the major WordPress SaaS hosting services such as WPENGINE, CLOUDWAYS, SITEGROUND, GODADDY, PANTHEON, PAGELY, FLYWHEEL, BLUEHOST etc. As long as they allow you to temporarily install a backup/restore plugin, you’ll be able to import your site into DevelopVIDeploy.

Internally, we use UPDRAFT PLUS (the premium version) but you can use whatever back/restore/transfer plugin you like.

Here’s a general idea of the process we use with UPDRAFT PLUS.

Note that some sites are unique and will require additional steps but these generally work for most standard sites:

1.  Install Updraft Plus on the old site. Make a backup with it.
2.  Download the backup files from Updraft Plus (it makes you download them one at a time so you’ll probably have to download five or more files – just make sure you get them all).
3.  Create a new site on one of your DVI servers using the domain you’re transferring and then point the DNS of the old site to it. THIS WILL TEMPORARILY disconnect your old site from the internet.
4.  Enable SSL on the DVI SSL tab for the new site.
5.  Install Updraft Plus on the new site.
6.  On the new site, upload the backup files using the UI that Updraft plus provides in its admin area. (If the files are too large you will need to upload them using sFTP instead to the Updraft Plus backups folder).
7.  Restore the site using Updraft Plus. It handles the database including table name changes and so on.
8.  Compare your old wp-config.php file with your new wp-config.php file and make sure any non-standard entries are moved over. For most sites this isn’t an issue but some sites have plugins that have custom wp-config entries.

Note that for step 3, it might take a bit for the DNS to propagate and allow access to the newly created site. But if you have a proxy service such as CloudFlare, it should only take a minute or two at most.

The above steps work for non-critical sites that can handle some down time. If you have sites that cannot handle a lot of down-time the process is a little more complicated:

## For Sites That Cannot Handle A Lot Of Down Time

1.  Make sure that the domain of the original site is connected to a proxy dns such as Cloudflare. The reason for this step is to allow for IP changes in the DNS that are almost instantaneous instead of having to wait for DNS changes to propagate.
2.  Install Updraft Plus on the old site. Make a backup with it.
3.  Download the backup files from Updraft Plus (it makes you download them one at a time so you’ll probably have to download five or more files – just make sure you get them all).
4.  Create a new site on one of your DVI servers with a temporary domain.
5.  Point your DNS for the temporary domain to the server’s IP.
6.  Enable SSL for the temporary domain on the DVI SSL tab for the new site.
7.  Install Updraft Plus on the new site.
8.  On the new site, upload the backup files using the UI that Updraft plus provides in its admin area. (If the files are too large you will need to upload them using sFTP instead to the Updraft Plus backups folder).
9.  Restore the site using Updraft Plus. It handles the database including table name changes and so on. It will also change the domain of the imported site to the temporary domain.
10.  Compare your old wp-config.php file with your new wp-config.php file and make sure any non-standard entries are moved over. For most sites this isn’t an issue but some sites have plugins that have custom wp-config entries.
11.  When you are ready to make the change permanent, use the DVI DOMAIN CHANGE feature to change the domain back to the original domain.
12.  If your original site is an ecommerce site or collects other data (such as user registrations), deactivate it or shut it down – this will prevent users from inadvertently entering data into it.
13.  Point the DNS of the updated domain to the IP of the server where the new site is located. This will **DISCONNECT** your old site from the internet – you’ll need to wait for the DNS changes to propagate. (If you are using CloudFlare, the DNS changes should just take a few seconds.)
14.  Request a new SSL certificate in the DVI SSL tab for the site.

## Notes

*   Some backup/restore and import plugins and techniques can sometimes change the WP folder permissions. You’ll notice this if you create an sFTP user and try to change a file or delete a file – you’ll get a permission error. Just use our RESET PERMISSIONS tool under the site TOOLS tab to resolve this issue.
*   Some backup/restore and import plugins add entries to the _wp-config.php_ file using double-quotes. We expect single-quotes to be used. When reading the _wp-config.php_ file for database and other information during operations such as backups, clones, restores, etc. double-quotes will cause errors. So please double-check your _wp-config.php_ file to verify that they are indeed using single-quotes instead of double-quotes after importing sites.
*   Many hosts have custom plugins that help them manage the sites on their infrastructure. After importing, you should delete those plugins – especially the ones in the _wp-content/mu-plugins folder_ (if such a folder exists)

## Premium Help

Prefer to have someone else handle site migrations for you? Check out the bottom of our [services page](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/premium-services/) for our Site Transfer Service pricing.

- - -

## Alternatives

[How to use MIGRATE GURU to migrate sites to DevelopVIDeploy](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/use-migrate-guru-to-quickly-move-sites-to-wpclouddeploy/)

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529152702/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
