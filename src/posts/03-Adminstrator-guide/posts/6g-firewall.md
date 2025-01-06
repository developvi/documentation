---
title: "6G Firewall (Deprecated)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: 6G Firewall (Deprecated)
  parent: 03-Adminstrator-guide
  order: 3
---

Note: The 6G Firewall has been replaced by the [7G Firewall](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/7g-firewall/). New servers and sites will not see the 6G Firewall option.

- - -

The “6-G” firewall is actually just a set of web-server rules (originally published by [Perishable Press](https://web.archive.org/web/20240420005716/https://perishablepress.com/)) to filter out some well-known bad traffic before the requests hits the WordPress site. The idea with this type of “firewall” is that traffic requesting PHP/WordPress resources is expensive. It’s much cheaper and faster to weed them out at the webserver level before it gets that far.

One of the draw-backs of this type of firewall is that certain activities that are legitimate will get blocked. So we’ve provided a way to enable or disable portions of the rules.

To enable the entire rule set:

*   Go to DevelopVIDeploy → Applications
*   Click on the site for which this action will apply
*   Click on the _6GWAF_ tab
*   Toggle the _Enable or Disable ALL 6G Rules_ switch
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

After the full rule set is enabled, you can disable portions of the rules using the rest of the toggle buttons on the screen.

## Notes & Issues

### Easy Digital Downloads

Some “add-to-cart” URLS in Easy Digital Downloads will fail with the 6G Firewall enabled. In particular, direct urls with square brackets embedded in them. These URLs are usual constructed when you have products with multiple price options and you want to give the user a direct link to one of the price options. They look something like this:

https://simple-press.com/checkout?edd\_action=add\_to\_cart&download\_id=81486&edd\_options\[price\_id\]=1

You can see the square brackets at the end of the URL.

There are two ways to work around this:

1.  Turn off the REQUEST STRING rules portion of the 6G firewall. You can do this under the 6G WAF tab.
2.  If you would like to keep most of the REQUEST STRING rules you can edit the _/etc/nginx/common/6g.conf_ file to make the following changes:

Search for this in the _Request Strings_ section of the file.

"~\*(~|\`|<|>|:|;|\\\\|\\s|\\{|\\}|\\\[|\\\]|\\|)" 7;

Replace it with this:

"~\*(~|\`|<|>|:|;|\\\\|\\s|\\{|\\}|\\|)" 7;

Then, restart the nginx engine:

service nginx restart

## Colons In The Request Strings

Sometimes, request strings might have colons in them. This will be blocked by default since it is an uncommon scenario. Here’s an example legitimate request string that will be blocked:

https://simple-press.com/?edd\_action=get\_version&license=4xasebadfasreasdfljerr&version=2.1.0&item\_id=3916&author=Simple:Press

Notice at the end of the string the author is “simple:press” with a colon? This means that the entire request will be blocked, even though, in this case, it is a legitimate request.

There are two ways to work around this:

1.  Turn off the REQUEST STRING rules portion of the 6G firewall. You can do this under the 6G WAF tab.
2.  If you would like to keep most of the REQUEST STRING rules you can edit the _/etc/nginx/common/6g.conf_ file to make the following changes:

Search for this in the _Request Strings_ section of the file.

"~\*(~|\`|<|>|:|;|\\\\|\\s|\\{|\\}|\\\[|\\\]|\\|)" 7;

Replace it with this:

"~\*(~|\`|<|>|;|\\\\|\\s|\\{|\\}|\\\[|\\\]|\\|)" 7;

Then, restart the nginx engine:

service nginx restart

You will notice that the new specification string removes the “:” from the invalid characters list.

## PHPMyAdmin

PHPMyAdmin will be blocked by the 6G Firewall. If the it is turned on you should turn off the “QUERY STRING” rules section before launching it. After you are finished you can turn that section of the rules back on.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [7G Firewall](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420005716/https://developvideploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
