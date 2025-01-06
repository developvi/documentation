---
title: "Site Expiration"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Site Expiration
  parent: 03-Adminstrator-guide
  order: 21
---
An admin can set an expiration date on a site or one can be set automatically when the site is created.

Admins can set what will happen to expired sites – there are four choices:

*   Automatically delete the site
*   Password protect the site
*   Apply an admin lock to the site
*   Disable the site

- - -

## Manually Set an Expiration Date

To set an expiration date:

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the site you want to work with and click on the title – this will bring up the site details screen
*   Locate the **SITE EXPIRATION** metabox on the right hand side of the screen
*   Set the date and time for the expiration
*   Scroll up and click the UPDATE button.

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-01.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-01.png)

- - -

## View Expired Sites

Sites that are expired but not deleted will have labels automatically applied to them in the site list:

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-03.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-03.png)

Additionally, you can quickly filter the site list to view expired sites:

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-05.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-05.png)

- - -

## Configure Site Expiration Behavior

As mentioned earlier there are four options that can apply to a site when it expires. You can set these in the SETTINGS area.

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the **SITE EXPIRATION** section
*   Check the boxes for the actions that will apply when a site expires
*   Scroll down and click the **SAVE SETTINGS** button.

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-06.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-06.png)

- - -

## Automatically Set Expiration Dates for New Sites

When you create a new site you can automatically set an expiration date for it.

To do this you use [SITE PACKAGES](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/).

Site packages have an **EXPIRE SITE** option. If this is set and the site package is used when creating a site, the new site will automatically have an expiration date calculated and applied to it.

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-08.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-08.png)

- - -

## Unexpire a Site

If a site is expired (and not deleted of course), you can un-expire it:

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the site you want to unexpire and click on the title – this will bring up the site details screen
*   Locate the **SITE EXPIRATION** metabox on the right hand side of the screen
*   Unset the **HAS SITE ALREDY EXPIRED** checkbox
*   Change the expiration date to something far into the future (otherwise our background process will evaluate the existing date and expire the site again)
*   Scroll up and click the UPDATE button.

- - -

## Force a Site To Expired Status

You can force a site to be tagged as ‘expired’. **However, the rules for an expired site (such as applying an admin lock or password protecting the site) will not be executed.** The only effect this action will have is to tag the site as expired – it will also show up in the site list as expired with the associated labels.

To force a site to expired status:

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the site you want to unexpire and click on the title – this will bring up the site details screen
*   Locate the **SITE EXPIRATION** metabox on the right hand side of the screen
*   Set the **HAS SITE ALREDY EXPIRED** checkbox
*   Scroll up and click the UPDATE button.

- - -

## Site Expiration & Quotas

You can combine Site Expirations with [Disk Quotas](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/) and [Custom Post Type Quotas](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/) in an interesting way.

You can set a site expiration when a quota is exceeded – example, 30 days. This allows the site to stay up for a period of time after the quota is exceeded. Then, when the expiration date arrives, stricter expiration rules can apply (such as deleting the site or locking it.)

- - -

## Bulk Actions

Two bulk actions are optionally available in the site list.

To use these actions you must first enable them in SETTINGS:

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the **SITE EXPIRATION** section
*   Enable the **BULK ACTION** checkbox
*   Scroll down and click the **SAVE SETTINGS** button.

Now you should see two new items in the BULK ACTIONS menu in your site list:

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-15.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-15.png)

- - -

## WooCommerce Integration

You can set a site package for a WooCommerce product. This means that IF the site package has an EXPIRE SITE value, it will apply to new sites when the product is purchased and the new sites will have an expiration date.

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-12.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-12.png)

One thing to keep in mind is your setting for what happens when a site is expired. If you set the option to delete the site, it is possible the site will be deleted but your customer’s subscription will still be in effect.

Thus, it is better to create subscription products with one time payments if you intend to delete the site when it expires. You can do this by setting the subscription payment to zero but using a one time fee and automatically cancelling the subscription after 1 month:

[![](https://web.archive.org/web/20240420003952im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-10.png)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-site-expiration-10.png)

You can, of course include this product in a GROUPED product so that the customer can have the option to upgrade to a real subscription before the site expires.

### Integration With Cancellation

When a site is cancelled, you can specify that it is set to ‘expired’ after X days instead of being deleted right away. Then, for your ‘expiration’ options, you can specify that the site is to be deleted.

This allows you to give your customers a grace period to change their minds about the cancellation.

- - -

_Availability: Requires DevelopVIDeploy 5.7 or later._

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [White Label Colors](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420003952/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
