---
title: "Force The Use of WWW On A Website"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Force The Use of WWW On A Website
  parent: 08-tips-techniques-education
  order: 9
---
Sometimes you want to force the use of WWW in front of your domain. There is generally very little difference on a site using a WWW prefix vs not using it. There are two reasons though why you might want to force it:

*   “www” stores cookies for the domain and all subdomains. Without www, separate cookies are stored for each subdomain. So, for large sites with many requests going between subdomains it might be a tab bit faster when using “www”
*   An existing site already uses “www” and simply wants to continue doing so to preserve SEO rankings & links

To force the use of WWW, just update your WordPress records on the WordPress settings screen.

*   Go to **SETTINGS** → **GENERAL**
*   Add the ‘www’ in the _WordPress Address_ and _Site Address_ fields.

[![](https://web.archive.org/web/20240304143847im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/changing-wp-to-www-prefix.png)](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/wp-content/uploads/2020/12/changing-wp-to-www-prefix.png)

You can confirm that the change has been made by going to the permalinks screen:

*   Go to **SETTINGS** → **Permlinks**
*   Each permalink option should show the “www” in it.

Click the SAVE CHANGES button to update your permalinks.

You may need to update your DNS pointers as well to create a WWW entry.

## Moving between HTTP and HTTPS

When you switch between HTTP and HTTPS (or vice-versa), we update the domain back to its default. So, you will need to make the change twice.

First, add the ‘www’ before turning on HTTPS. This allows us to get a certificate for both ‘www’ and non-www domains.

After HTTPS is turned on, go back and add ‘www’.

## Search and Replace

If you’re going from a “mydomain.com” to “www.mydomain.com” then you’ll want to use a WordPress search and replace tool to conduct two search & replaces on your database:

*   Search for “http://mydomain.com” and replace with “http://www.mydomain.com” (or “https://www.mydomain.com” if using ssl)
*   Search for “https://mydomain.com” and replace with “https://www.mydomain.com”

_Do **NOT** search for just “mydomain.com” and replace with “www.mydomain.com”. If you do you might end up with entries such as “http://www.www.mydomain.com”._

We have a simple search and replace tool in the SITE detail screen. But for more sophisticated search & replace function we use the search and replace tool in UPDRAFT PLUS (which is our backup plugin). There are other 3rd party tools that can be used to do this as well.

## Other Notes

Don’t forget to set up your CNAME for the “www” prefix in your DNS if it’s not already present!

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240304143847/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
