---
title: "Native Linux Cron"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Native Linux Cron
  parent: 03-Adminstrator-guide
  order: 5
---
WordPress has a scheduler that allows processes to run on a periodic basis. However this scheduler has two fatal flaws:

1.  It only runs when there is activity on the site. This means that if a process is scheduled to run at 1:00 pm but no activity has occurred around that time-frame, the process will not run until someone uses the site.
2.  Because it runs every time there is activity on the site, it uses up resources on every request for a page/post/object. For sites with a lot of simultaneous users or heavy activity, it’s a lot of unnecessary overhead.

However, there is a way to make sure that WordPress runs scheduled tasks without missing them and without unnecessary overhead. It involves setting up a native Linux Cron (“cron” is the Linux scheduler.)

To enable this:

*   Go to DevelopVIDeploy → All Apps (or DevelopVIDeploy → WordPress Sites)
*   Click on the site for which you need an SSL certificate
*   Click on the _Crons_ tab
*   Select an interval – this is how often the native Linux cron will force WordPress to check to see if scheduled tasks need to be run. The lower the interval the more load on the site. But, some sites do need a 1 minute interval so it’s available as an option – if yours do, then choose that. Otherwise choose 15 mins or 60 mins.
*   Click on the toggle switch and then click the _OK_ button on the confirmation message

## Notes

*   Some plugins try to be helpful and will throw a warning in the wp-admin area that CRON is disabled (because a constant is added in wp-config.php to disable the WP CRON.) These messages can be safely ignored if the LINUX Cron is configured.
*   When you activate CRONs on a multisite installation of WordPress, the cron process will loop through and trigger on each sub-site. If you set your interval to _1 minute_ then you’ll be doing this every minute, **causing a ton of load on your installation**. Think very carefully about activating a native Cron on a Multisite installation of WordPress. And, if you do decide that it is appropriate, whether you can use a larger interval such as 15 or 60 minutes. The more sub-sites you have, the more critical this decision will be for performance.

- - -

## Using the WP CRONTROL Plugin To Monitor WP Cron Jobs

The [WP CRONTROL](https://web.archive.org/web/20240304161209/https://wordpress.org/plugins/wp-crontrol/) plugin is a great tool that allows you to view WP cron jobs.

Once installed, go to the TOOLS → CRON EVENTS screen.

In there you should see a full list of WP Cron jobs and the next time that each will run. If you see a lot of them with the NEXT RUN set to ‘due now’, it likely means the Linux Cron isn’t working properly.

- - -

## Learn More

You can learn more about how WP handles CRON JOBS in our [ALL ABOUT WP CRONS](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/articles-parent/all-about-wp-crons/) help article.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/7g-firewall/)
*   [Disabling Sites](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304161209/https://wpclouddeploytation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
