---
title: "Theme & Plugin Updates"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Theme & Plugin Updates
  parent: 03-Adminstrator-guide
  order: 33
---
## Introduction

In DVI Version 4.9, we added a new feature to allow the admin to trigger update of themes, plugins and even WordPress, from inside the WP dashboard. And in Version 4.10 we improved it by adding a couple of other tweaks.

This feature will be useful for agencies to use on sites that are not critical and can handle some downtime. For many agencies, that’s 90% or more of the sites under management. So judicious use \[of this feature\] can help you to quickly power through updates.

You can find the update tools in the SITE UPDATES tab for your site.

[![](https://web.archive.org/web/20231207105713im_/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-150-1.png)](https://web.archive.org/web/20231207105713/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-150-1.png)

This feature is not intended as a replacement for site management tools such as MAIN WP or for the built-in auto-updates in WP. But, if, for some reason you prefer not to use those types of site management tools, then these basic functions can be used to update your sites on demand, one at a time or in bulk.

## General Features

*   You can choose to update everything or just some things: eg: just WordPress, just themes, just plugins or just themes & plugins.
*   You can specify a global list of plugins and themes to exclude from updates which will apply to all sites and all update operations.
*   Backups are taken automatically before any updates.
*   An image of the home page is taken before any updates and another is taken afterwards. If there are more than 1000 pixels difference between the two images, the site is restored from the backup. You can change the threshold from 1000 to any other number. **To make this feature work you need to sign up for a 3rd party service that helps us compare the images.** See the “Verifying Updates” section below for links to the 3rd party service.

[![](https://web.archive.org/web/20231207105713im_/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-151.png)](https://web.archive.org/web/20231207105713/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-151.png)

However, probably the most powerful feature is the bulk updates.

[![](https://web.archive.org/web/20231207105713im_/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-152.png)](https://web.archive.org/web/20231207105713/https://developvideploy.com/wp-content/uploads/2021/08/wpcd-v4-152.png)

Combined with automatic backups before updating and an automated visual check of the home page after updates, most of your non-critical sites can be updated with just a few clicks.

And, because we provide such flexible filters at the top of the site list you can do things such as:

*   Run updates for all sites on servers at a particular provider
*   Run updates for all sites on a particular server
*   Run updates for all sites located in a particular region
*   Run updates for all sites using a selected PHP version
*   Run updates for all sites with certain tags/groups

Tip: If you have sites that you do not want to include in group updates, you can add them to a color-coded GROUP. Then when you apply your filter (or select all sites), you will instantly recognize those color-coded tagged sites and be able to unselect them.

## Verifying Updates

We use the [https://htmlcsstoimage.com/](https://web.archive.org/web/20231207105713/https://htmlcsstoimage.com/) service to take a screen shot before and after updates are complete. An image of the home page is taken before any updates and another is taken afterwards. If there are more than 1000 pixels that are different between the two images, the site is restored from the backup. You can change the threshold from 1000 pixels to a higher or lower value on the settings screen: **DevelopVIDeploy → APP:WordPress Settings → Theme & Plugin Updates**.

To use this service you need to sign up for an account and fill in the API USER NAME and API KEY on the **DevelopVIDeploy → APP:WordPress Settings → Integrations** tab.

## Backups

We attempt to create a backup before updating the site. If you’d like to make sure that your backups end up on your AWS bucket, then you should ensure that you configure backups for the entire server (or for each of your sites) prior to initiating update operations.

If you do not configure backups, there will be errors in the logs but we will not stop the update process. And any backup files created in this instance will remain on the disk only.

Additionally, please ensure that your RETENTION days value is NOT set to ‘-1’. The ‘-1’ value indicates that no backups should be left on the local disk. If ‘-1’ is used for your retention days and we have to restore a site, there will be no local backups to restore from.

We use our [basic backup scripts](https://web.archive.org/web/20231207105713/https://developvideploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/), not our [advanced backup scripts](https://web.archive.org/web/20231207105713/https://developvideploy.com/documentation/command-line-scripts/advanced-backups/) for these backups.

Bonus: If updraft-plus is installed we will attempt to trigger a backup using its wp-cli command as well.

## Caches

We attempt to clear caches after updates. If certain well-known cache plugins are installed AND their corresponding wp-cli extensions are also installed, we’ll use wp-cli to invoke the plugin to clear their cache.

The cache plugins we’ll attempt to clear are:

*   WP-Rocket
*   WP Super Cache
*   WP Total Cache
*   WP Fastest Cache

We cannot always reliably detect when these plugins and their associated WPcli extensions are installed so you might sometimes see errors as we attempt to invoke them. If the plugin is not installed on the site you can ignore those errors.

## Global Excludes

The DVI settings screen has two options that allow you to exclude themes and plugins from being updated.

[![](https://web.archive.org/web/20231207105713im_/https://wpclouddeploy.com/wp-content/uploads/2021/09/wpcd-v4-154.png)](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/wp-content/uploads/2021/09/wpcd-v4-154.png)

If an exclusion list is supplied, updates will be slower.

## Restoring

### Testing Restores

If the comparison of the images taken before and after an update fails, we will try to restore the site from backup. If the backup failed for any reason then this might not be possible and you will have to manually restore the site from an older backup.

### Very Active Sites

If you have a site where data is constantly being added, you might not want the automated restore to kick in. The automated restore might cause you to lose data that was created between the start of the backup and the end of the update. For these sites it’s better to handle the updates manually (or modify our update script to prevent restoring data on those sites.)

## Other Important Notes

*   If your domain has SSL enabled, then its non-ssl address should be redirected. i.e.: http:// re-directed to the https://. Otherwise we will end up taking a snapshot of the incorrect domain before and after the backup.
*   If you have duplicate domains (even if the sites are on different servers), updates will not callback and complete properly. For those domains you will need to:
    *   Check the COMMAND LOG screen to verify that they are complete
    *   Manually mark the task in the PENDING LOG screen as complete.
    *   Use the TOOLS tab on the site to CLEAR BACKGROUND PROCESSES.
*   There is a timeout set for all long running commands such as creating a new server, backups and so-one. That timeout is in effect for updates. It is possible that very large sites might need longer than the default 15 minutes for backups and updates to complete. If that’s the case you can temporarily increase the timeout value in the SETTINGS screen.

## Performance Notes

*   Sites are processed sequentially per server. Only one site at a time is processed for each server. If you have a lot of servers and sites, it could take a while to chug through all of them. To be clear, we will handle multiple servers simultaneously – but we will only attempt to update one site at a time on each server.
*   If you have a lot of servers and you plan on simultaneously updating sites on all of them, make sure that the server DVI is running on has enough horsepower (and is configured) to handle many simultaneous PHP threads – otherwise the REST API callbacks that help mark a task as finished might timeout as they wait for an available thread. If that happens you will need to manually mark the tasks as complete and reset the site metadata (see the IMPORTANT NOTES section above).

## Troubleshooting

When doing bulk updates, your best troubleshooting tools are the COMMAND LOG and PENDING LOG screens.

*   On the PENDING LOG screen you will see all the bulk actions that are scheduled and their status. Anything that is “in-process” for a long time has probably failed.
*   The COMMAND LOG screen will show the output for each update on each site. There will be one row for each site update. Any errors encountered will be shown here. If there is an item in the COMMAND LOG that shows completed but whose associated PENDING LOG record is stuck, you can manually update the PENDING LOG record to “complete” and clean out the in-process metas on the site record.

## Testing The Restore Process After A Failed Update

If you’d like to force a failure for an update so you can see how a site is restored, we’ve got you covered. Set the variance pixel count to -1 on the **DevelopVIDeploy → APP:WordPress Settings → Theme & Plugin Updates** tab to always force a restore after update.

This works because a negative number will always return a failed status when comparing the before and after images – even if zero pixels have changed it would still be greater than -1.

## Unique DVI Features

One of the biggest issues with SaaS systems is that you can’t easily customize the WP update process. So after an update you find yourself doing things like flushing various caches using the different cache plugins your clients have on each site. Maybe disabling and re-enabling plugins to force them to recognize new WP features and so on.

With DVI you can modify the scripts directly to add these actions so that they get done for you automatically! It’s the ultimate in customization and is likely to save you a TON of time!

## Permanent Beta

We are keeping this feature in permanent beta status because there are just way too many things that can go wrong. If you’re an agency that’s worked with WordPress for a while, you already know that when it comes to WP updates, nothing can be taken for granted. They generally work but can fail for odd and, sometimes, very silly reasons.

Therefore as with all computer systems you should make sure that you perform regular backups and especially do so before an update.

Some examples of things that can go wrong:

*   The server runs out of diskspace in the middle of the update.
*   We use wp-cli for updates and sometimes plugins and themes throw errors when this is invoked, which can, at times, prevent the updates from starting or completing.
*   The automatic restore might fail for various reasons and certain customized configuration files might not be restored automatically even when the restore has otherwise worked.
*   The threshold pixel difference count for determining whether an update was successful is tricky – we have defaulted it to 1000 but it might take you some trial and error to determine if that number should be higher or lower for your constellation of sites.
*   The before and after image snapshots might get an incomplete image of the site’s home page because the site takes too long to load or has a ton of JS code that needs to render the page properly.
*   There might be domain resolution issues (whether temporary or permanent) that prevents us from getting before and after images or that points us to the wrong site or no site at all.
*   A plugin or theme might require an updated version of PHP which causes the site to crash after an update.
*   And updated plugin or theme is simply incompatible with an existing plugin or theme and causes the site to crash after the update.
*   WP refuses to process the update because it detects permission errors on the files/folders.
*   A premium plugin or theme refuses to update itself because a license key is invalid or not present.
*   A premium plugin or theme cannot be updated because the license server cannot be contacted or is being blocked.
*   We have not tested this with MULTISITE.

If you’re using this feature one site at a time, it’s not much of an issue because you can see the feedback on the screen. But if you’re using BULK ACTIONS to handle multiple sites that’s a whole lot more difficult to manage when automated recovery is necessary.

This does not mean that the feature isn’t usable in production. By keeping it as a permanent beta we’re just reminding you that you need to pay attention to the updates as they occur and that you can’t blame DVI for everything that goes wrong with them.

## When To Ask For Support

If you have a site that you can update using the normal WordPress update screen but that is erroring out while updating using DVI, we definitely want to know about it. Most of the time the issue is likely to be a plugin or theme on the site that is not compatible with wp-cli. But if that’s not the case we’d like to figure out what else is going wrong. So please contact support – we can log in and take a look at the logs.

## Wrap Up

This is a powerful tool that you should use – but use it judiciously. As with anything related to updating a WordPress site, when an update works it’s great; when it doesn’t you just have to take a breath, sigh a little then buckle down to find the culprit(s) and deal with them. Just because this tool makes it easy for you perform updates does not mean you can just rest easy. WP updates are always a PITA – our tools just make them a little less so!

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Manage PHP Options](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Notifications and Alerts](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [Webserver Types](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [SSH Key Overrides](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [DVI Cron Jobs](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20231207105713/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
