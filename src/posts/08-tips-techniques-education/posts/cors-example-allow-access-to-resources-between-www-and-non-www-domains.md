---
title: "CORS Example Allow Access to Resources Between www and non-www Domains"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: CORS Example Allow Access to Resources Between www and non-www Domains
  parent: 08-tips-techniques-education
  order: 11
---
Lets assume you have a site where certain requests are being made from https://yourdomain.com for resources on https://www.yourdomain.com. And lets assume that, for some reason you do NOT want to issue a blanket redirect from one domain to another. And lets also assume that the request to https://www.yourdomain.com is being denied because CORS is not configured to allow the cross-origin request.

What does your CORS entry in your _/etc/nginx/sites-enabled/yourdomain.com_ file need to look like to enable this?

#Custom CORS rules for this site to allow for non www to request resources from www.
if ($http\_origin ~\* "^https?://(yourdomain.com|www.yourdomain.com)$") {
  set $cors\_origin $http\_origin;
}
add\_header Access-Control-Allow-Origin $cors\_origin;
#End custom CORS rules

This might seem needlessly complex. Why not just use add\_headers with the www and non-www domains?

Because NGINX will only allow a SINGLE _add\_header_ directive for _Access-Control-Allow-Origin_. Which does not work because you need to process requests from both www and non-www origins.

So, we use an IF statement to check the incoming origin and then set a variable (in this case $cors\_origin) if the condition is satisfied. Then, we use a single _Access-Control-Allow-Origin_ to reference the URL set in the variable. If the variable is empty, NGINX does not send a header.

## DVI Specific Considerations

Something specific to DVI is this: If you’re hoping to address media, js and other css files that are being cached in the browser, you need to add the CORS directive to the /_etc/nginx/common/browsercache.conf_ file as well!

Why?

Because of an NGINX quirk. The /_etc/nginx/common/browsercache.conf_ file contains just one _add\_header_ directive to tell the browser to cache things. But, because of this, NGINX will drop all the _add\_header_ directives in the parent SERVER{} block instead of inheriting them. grrrr…it’s just something you need to be aware of and deal with. And yes, this behavior is documented deep within the bowels of the NGINX documentation.

There could be several add\_header directives.
These directives are inherited from the previous configuration level if and only if
there are no add\_header directives defined on the current level.

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [Import Sites](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420002018/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
