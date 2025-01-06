---
title: "Manage PHP Options"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Manage PHP Options
  parent: 03-Adminstrator-guide
  order: 10
---
WPCloud Deploy offers a bunch of PHP options you might need for certain sites – without forcing you onto the command line.

## Change PHP Version

*   Go to WPCloud Deploy->Applications
*   Click on the site for which this action will apply
*   Click on the _PHP_ tab
*   Scroll down to the _CHANGE PHP VERSION_ section
*   Select your new PHP version in the drop-down – we currently support up to 8.2
*   Click the _Change PHP Version_ button.
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

## Restart the PHP Service

*   Go to WPCloud Deploy->Applications
*   Click on the site for which this action will apply
*   Click on the _PHP_ tab
*   Scroll down to the _RESTART PHP SERVICE_ section
*   Click the _RESTART_ button.
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

## Set Common PHP Options

The most common PHP options that admins need to change are:

*   UPLOAD\_MAX\_FILESIZE
*   POST\_MAX\_SIZE
*   MEMORY\_LIMIT
*   MAX\_EXECUTION\_TIME
*   MAX\_INPUT\_TIME

You can change all these values without leaving the DevelopVIDeploy admin screen.

*   Go to WPCloud Deploy->Applications
*   Click on the site for which this action will apply
*   Click on the _PHP_ tab
*   Scroll down to the _ADD OR UPDATE SOME COMMON PHP OPTIONS_ section
*   Select one of the five options from the drop-down in the section
*   Enter a value for the option
*   Click the _SET THE SELECTED OPTION_ button.
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

## Set A Random PHP Option

There are dozens of other PHP options that can be changed or set. We provide a user interface for you to specify any PHP option along with an associated value.

_Warning: This is a power-user feature. Set the wrong option or enter a bad value and your site can fail to load! Use it wisely!_

*   Go to WPCloud Deploy->Applications
*   Click on the site for which this action will apply
*   Click on the _PHP_ tab
*   Scroll down to the _\[DANGER ZONE\] ADD OR UPDATE A PHP OPTION_ section
*   Enter the PHP Item you want to add or change in the _php.ini item_ field
*   Enter the value for the item in the next text box
*   Click the _SET THE SELECTED OPTION_ button.
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

## Set PHP Workers

An ADMIN can change the number of PHP workers for a site.

_Warning: This is a power-user feature. Set the wrong option or enter a bad value and your site can fail to load! Use it wisely!_

*   Go to WPCloud Deploy->Applications
*   Click on the site for which this action will apply
*   Click on the _PHP_ tab
*   Scroll down to the _\[DANGER ZONE\] PHP WORKERS_ section
*   Set the PHP Workers Parametera as desired
*   Click the _UPDATE_ button.
*   Click the _OK_ option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

- - -

## Change The Max WordPress Upload Size

If you’re looking to change the maximum size allowed for file uploads into WordPress, the PHP option is not the only item that needs to be changed. You also need to change some NGINX options as well.

Because of this, we have a dedicated option for changing the Maximum upload filesize in WordPress.

You can find it at the bottom of the TWEAKS tab for your site.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304141443/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
