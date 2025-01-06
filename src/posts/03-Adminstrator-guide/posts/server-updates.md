---
title: "Server Updates"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Server Updates
  parent: 03-Adminstrator-guide
  order: 32
---
There are three types of server updates.

1.  Updates that involve our stack such as updating the NGINX configuration files or adding new packages
2.  Core Linux updates including security updates.
3.  Security-only updates for Linux

Updates can be accessed via the UPGRADES tab on any server.

**Note: We strongly suggest that you use your Cloud Provider’s tools to take a full snapshot or backup of your server before running any updates!**

## DVI Stack Updates

If there are any updates involving our stack you will see a notice on this tab along with instructions and any links to pertinent documentation.

## Core Linux Updates

Security updates are usually run automatically every night. However, there are additional non-security related updates that you can run – these are optional. Use the **RUN ALL LINUX UPDATES NOW** button to do this.

[![](https://web.archive.org/web/20240529140617im_/https://wpclouddeploy.com/wp-content/uploads/2021/08/wpcd-v4-127.png)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/wp-content/uploads/2021/08/wpcd-v4-127.png)

Clicking this button will immediately create a Linux Cron scheduled process to run the updates in the background. This includes both security and non-security updates.

One of the side-effects of running these updates is this: it will clear out the entry under the HEALTH column for that server in the server list. This column will then be updated overnight when the health script runs again.

To view the logs of any updates, use the options under the LOGS tab.

## Security Updates

As mentioned earlier, security updates are usually run automatically every night. However, you can force them to run immediately using the **RUN LINUX SECURITY UPDATES ONLY** button in the Upgrades tab on each server.

Additionally, you can run them in bulk from the server list screen as well.

## Notes

#### Update Count For Security Updates Stuck In The Health Column Over A Number Of Days

*   There are times it might seem as if security updates are not running. For example, in the health column you might see the same number of security updates available day-after-day. While security updates are automatically run every night which should reduce this number, sometimes they might be dependent on a regular update. In which case you’ll see that the same number of security updates are needed every single night.
*   The solution is to run all updates for your server.

#### Update Fails Repeatedly

*   You might need to schedule a server reboot first before applying updates. Just like Windows machines, prior updates that were applied might require the server to be rebooted before future updates can run. If you’re doing bulk updates, you might even see the update schedule attempt failed in the PENDING LOGS screen.
*   If updating via the BULK ACTIONS option fails for a server, try running it from the standard UPGRADES tab inside the server detail screen.
*   Sometimes, servers simply need to be restarted before updates will run. If it seems as if the updates are not running please restart the server(s) and then send the update request again.

#### Update Requires Input

One of the issues with updates is that sometimes they require user input. Most updates run just fine in the background but once in a while you get an update that requires user input. There’s no way to know if this is case ahead of time. Instead, you’ll likely see that the update counts are “stuck” or are simply not running no matter what you do. In this case you’ll have to run them from the command line.

#### Server Updates When Server Is First Deployed

We offer the option to run updates immediately after the server is provisioned. This is done on a best-efforts basis. Sometimes, not all the updates can be run without a server restart. So we cannot guarantee that all the updates will run immediately after the server is first started.

## **Other**

**We strongly suggest that you use your Cloud Provider’s tools to take a full snapshot or backup of your server before running all updates!**

The UPDATES function is provided as a convenience and most of the time it works. But if certain updates require a server restart before they will work or require user input then it will seem as if they’re not running at all. Ultimately, the best way to run updates is from the SSH command line, especially when the items mentioned above do not work.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529140617/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
