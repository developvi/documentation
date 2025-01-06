---
title: "Site Update Plans"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Site Update Plans
  parent: 03-Adminstrator-guide
  order: 20
---
## Introduction

**Site Update Plans** are used to push files and certain configuration updates out to multiple sites simultaneously.

This feature is most useful when using WordPress as the foundation for your SaaS and is only available if our [WooCommerce](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/lp/sell-wordpress-site-subscriptions-with-woocommerce/) add-on is active.

As you might already know, there are three types of WordPress installations you can use for your SaaS: Multisite, Standard Sites and Multi-tenant sites (see [WordPress SaaS: Multi-tenant vs Multisite vs Standard Sites.](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wordpress-saas-multi-tenant-vs-multisite-vs-standard-sites/))

**Site Update Plans** are used for SaaS installations that are built on Standard Sites. They are not used for Multi-tenant sites since [multi-tenant WordPress sites have its own built-in update process with versioning and GIT integration](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/).

- - -

## What Business Problem Do Site Update Plans Solve?

Standard sites are stand-alone regular WordPress sites so when its time to update plugins and themes, you would normally have two options for updates:

*   Update each of them individually
*   Use a third party tool such as MAINWP or MANAGEWP to pull down theme and plugin updates directly from their source repositories.

In a SaaS built on WordPress neither option is not ideal because you might want to have more control over what gets updated and how. For example: you might have issues related to licensing, you might want to remove plugins and themes, update wp-config.php entries, delete files etc.

Update Plans gives you that flexibility.

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-01.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-01.png)

With it you can update the themes and plugins on your template site and push out the updated files to your tenant sites. All without getting involved with GIT – which can be very useful for SaaS builders who aren’t comfortable with GIT or other software development tools and processes.

Update plans are only available if you have the [Premium DevelopVIDeploy WooCommerce](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/lp/sell-wordpress-site-subscriptions-with-woocommerce/) Add-on active.

### Advantages of Update Plans

*   Update plans allow you to handle plugins and themes that use a ‘loose’ licensing scheme – i.e.: a licensing process that does not disable functionality if not enabled on a domain. 90% of plugins and themes follow this ‘loose’ licensing process. You can get the update files on the template site and push them out to tenant sites without needing to manually activate a license on the tenants. Note: This is NOT an invitation to avoid paying for licenses!
*   You can push more than plugin and theme files – you can push configuration items, other files that you can use in custom plugins and more.
*   It is a less regimented versioning and update process than Multi-tenant WordPress.
*   It includes an option to run backups before updates.

### Disadvantages of Update Plans

*   You can accidentally push more files than you intend so you have be very aware of what \[files\] are present in the template. You might need to create a bash script to strip out anything you might not need or is not appropriate on the tenant.
*   Because it’s less regimented in its update and versioning process than Multi-tenant WordPress, it’s easier to make mistakes.

- - -

## What’s in An Update Plan?

Update plans are composed of the following components:

*   Select sites to update – you can select sites by server (all sites on a server), server groups (all sites on all servers in a group) or site/app groups (all sites matching a group)
*   Apply APP GROUP labels to updated sites
*   Select which plugins are deactivated and / or activated (which helps when it’s time to remove old functionality from your SaaS and add new plugins)
*   Add or update wp-config.php entries (for example, new plugins might need wp-config.php entries or you might need to replace a compromised API key)
*   Add or update DVI metas (eg: add an update history note to the DVI site record)
*   Add or update site options
*   Files & Folders to be excluded from being pushed to the target sites
*   Run custom bash scripts on each site before or after they’re updated (for example, to delete unwanted files such as old plugins and themes, files copied from the template that aren’t needed, apply custom database updates etc.)

## What Gets Pushed During an Update?

When a site is updated using an update plan, it gets all of the following from the template:

*   WP Core files (which allows for updates to core)
*   Plugins
*   Themes
*   Uploads
*   Other files present in the template

What Does NOT Get Pushed?

*   wp-config.php
*   Folders that are explicitly specified to be excluded
*   Files that are explicitly specified to be excluded

- - -

## Create a Site Update Plan

To create an Update Plan:

*   Navigate to **WpCloudDeploy → Site Update Plan**
*   Click the **ADD NEW SITE UPDATE PLAN** button at the top of the page
*   Fill out the fields as needed
*   Click the UPDATE button.

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-02.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-02.png)

## Execute An Update Plan

After a plan is created, you execute the plan on the **COPY TO EXISTING SITE** tab of a template site.

*   Navigate to **WpCloudDeploy → All Apps** (or **WpCloudDeploy → WordPress Sites**)
*   Scroll down to your template site
*   Click on the template site title
*   Click on the **COPY TO EXISTING SITE** tab
*   Scroll down to the **EXECUTE UPDATE PLAN** section at the bottom of the tab
*   Select the plan from the drop-down
*   Click on the **EXECUTE PLAN – DRY RUN** button – this will show a list of all servers and sites that will be affected – review carefully to make sure that you are aware of which sites are going to be updated!
*   Select the plan from the drop-down again
*   Click the **EXECUTE** button

- - -

## Excluding Files & Folders

You have the option of excluding files and folders from being pushed from the template site.

Some files/folders you might want to exclude:

*   Cache Enabler caches
*   Page builder cache files (so that they don’t overwrite the target site cache files with the template caches)
*   debug.log
*   Backup Plugins local files

Here is an example of how we specified exclusions on one of our production networks:

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-09.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-09.png)

- - -

## Monitoring Update Plan Executions

After you have started a plan, you can view its progress in the SITE UPDATE PLAN HISTORY screen – **WpCloudDeploy → SITE UPDATE PLAN HISTORY.**

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-03.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-03.png)

If the plan is successful, a checkmark will appear next to the number in both the COMPLETED SERVERS and COMPLETED SITES colums.

You can also look at the PENDING TASKS screen to follow the progress of each individual server and site.

- - -

## Backups Before Updates

Update plans have an option to backup a site before updating it. There are some gotchas when enabling this option.

The default DVI backup configuration will store a certain number of backups on the server (‘local backups’). If you have not changed this then you will need to make sure that your server has a lot of free space to hold all the backups.

Alternatively, you can c[onfigure your backups so that they are always off-loaded to your S3 bucket](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/).

### Failed Backups

If a backup fails because of lack of disk-space, any sites in the update plan that have not been updated at that point will NOT be updated. You will need to either disable backups in the plan or fix the diskspace issue before resuming the plan.

To resume the plan you will need to mark the existing in-process PENDING TASK records as FAILED and then resubmit the plan.

- - -

## Timing

Sites are updated sequentially. On average we expect it to take 1-3 minutes per site after the template site has been pushed to a server. If backups are enabled, the time will increase for each site as the backup can take some time depending on the size of the site.

The key reason we don’t update in parallel is so that you can stop the updates at any time. The last thing you want is to have 100 sites being updated in parallel before you can change your mind.

If, you discover an issue midway through the update, you can remove the rest of the updates by deleting the pending tasks records.

The downside to this conservative approach, of course, is that, for larger installations, it can take multiple hours to complete updates to all sites.

- - -

## Related Videos

- - -

## Notes

#### All Files Pushed

*   Update plans push ALL files in the template other than wp-config.php and files and folders specifically listed to be excluded from the push. This means you might need to delete unwanted files in the tenant/target site after the update is complete. You can do this by creating a BASH script.

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-07.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-07.png)

#### Reactivating Plugins

*   Sometimes, you need to deactivate and reactivate a plugin to make the new version of a plugin update its data. You can do this by specifying the plugin in both the ACTIVATE THESE PLUGINS and DE-ACTIVATE THESE PLUGINS boxes. Deactivation occurs before activation so this will accomplish the reactivation of a plugin.

- - -

## Tips

### Plugins With Proprietary Update Notices

Some plugins will show an update notice in the admin area when an update is required. When an update plan pushes files, this update notice might not disappear. Usually the best thing to do is make sure that you specify that the updated plugin be deactivated and reactivated.

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-55-update-plans-10.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-55-update-plans-10.png)

In the above image you can see an example of how to do this – the same plugins have been added to the DEACTIVATE and ACTIVATE sections. This works because plugins in the DEACTIVATE section are always handled first, before plugins in the ACTIVATE section.

- - -

## Background Details on How the Updates Work

The updates work by first pushing a copy of the template site to the servers that are being updated. Each copy will have its own domain name.

When all servers have gotten a copy, the checkmark in the servers column will appear (see screenshot above).

You will see an entry for each server that will receive a copy of the template in the PENDING TASKS screen as soon as you start the plan.

[![](https://web.archive.org/web/20240304133827im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-04.png)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-55-update-plans-04.png)

After a template is pushed, additional entries will be added to the PENDING TASKS screen – one for each site on the target server. These tasks will handle copying files from the template clone to the destination site.

As things progress, you will see a lot of intermediate tasks added to the PENDING TASKS screen. Some of the task types you will see are:

*   execute-update-plan-push-template-to-server
*   execute-update-plan-get-data-after-push-template-to-server
*   execute-update-plan-get-data-after-template-domain-change
*   execute-update-plan-update-site-files
*   execute-update-plan-get-data-after-update-site-files
*   execute-update-plan-get-data-after-update-site-files

An explanation of the full sequence of tasks is in the [Site Update Plan – Pending Task Technical Notes](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/) document.

Note: Template copies can (and should) be deleted after the plan is completed (regardless of whether all sites or only a portion of sites were updated).

- - -

## Related Articles

[DevelopVIDeploy v5.5.0 Release Notes](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/whats-new-in-wpclouddeploy-5-5-0/)

[DevelopVIDeploy v5.6.0 Release Notes](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/whats-new-in-wpclouddeploy-5-6-0/)

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Expiration](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304133827/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
