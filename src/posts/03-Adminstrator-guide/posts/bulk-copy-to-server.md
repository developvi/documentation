---
title: "Bulk Copy To Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Bulk Copy To Server
  parent: 03-Adminstrator-guide
  order: 41
---
You can copy multiple sites from across multiple servers to a single server. However, as you might expect, there are a number of important stipulations before you can initiate this operation.

1.  The source sites must be on servers with the same web server as the target server. i.e.: you cannot copy NGINX sites to a server running OpenLiteSpeed and vice-versa.
2.  The target server must have no other activities occurring on it (e.g.: an admin must not be deleting sites or a customer site being created on the target server.)
3.  Recommended: The target server should be a clean server with no existing sites on it. While not a strict requirement, it will make things easier if you run into errors.
4.  The Server Sync premium module must be installed.

Since this is an operation that is not normally something you do day-to-day we’ve made it a multi-step operation restricted to DVI admins. You will not be able to offer this feature to your customers on the front-end.

## Step 1: Setup Target Servers

You setup your target or destination servers in SETTINGS. You can set up more than one server if you’re rebalancing multiple servers in one sitting. But, for most users, we expect that only a single server will be required.

*   Navigate to **DevelopVIDeploy** → **SETTINGS** → **APP: WORDPRESS SETTINGS** → **SERVERS**
*   Scroll down to the **BULK COPY TO SERVER** section
*   Add your target server(s) in the **TARGET SERVERS** field
*   Scroll down and click the **SAVE SETTINGS** button.

[![](https://web.archive.org/web/20240420012453im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-01.png)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-01.png)

## Step 2: Select Sites from the Site List

Next, you select your sites from the site list – we have a lot of filters that allow you to filter down to a list of sites. Again, for most users you’re likely copying all or a portion of sites from a single server over to a new one. So you can filter the site list by server.

But, of course, you can apply any filter selection and select sites as needed – even across multiples servers using APP GROUPS.

## Step 3: Initiate Operation

Once you’ve selected your sites, you can use the new options under BULK ACTIONS to copy the sites to your target server.

For each server you setup in step 1, you’ll see a new bulk action:

[![](https://web.archive.org/web/20240420012453im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-03.png)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-03.png)

When you choose a **COPY SITES TO SERVER** action, it will setup a series of records in **PENDING TASKS** – one for each site. The sites will then be copied one-by-one and marked completed. You will be able to see the progress by refreshing the \[pending tasks\] screen.

[![](https://web.archive.org/web/20240420012453im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-04.png)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-v57-bulk-copy-to-server-04.png)

## Step 4: Clean up

Once you’ve verified that the sites work on the target server(s), you should delete the original sites. This prevent duplicate domains from appearing in the site list.

- - -

_Availability: Requires DevelopVIDeploy 5.7 or later._

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420012453/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
