---
title: "Disabling Sites"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Disabling Sites
  parent: 03-Adminstrator-guide
  order: 6
---
You can completely disable a site – preventing users from reaching it and turning off all scheduled processes. The files will still exist on the server but the site will be lost to the world until you re-enable it.

To do this:

*   Go to DevelopVIDeploy → Applications
*   Click on the site for which this action will apply
*   Click on the **MISC** tab
*   Scroll down to the **ENABLE/DISABLE SITE** section
*   Click the **S****ite Status** toggle.
*   Click the **OK** option on the confirmation popup

After a while the screen will refresh – if the operation is successful. If the operation fails, you’ll get a popup message.

You can see a full log of the operation under the SSH LOG screen.

- - -

## Notes

When a site is disabled, if your DNS for the domain still points to the server, visitors will receive a generic NGINX or OpenLiteSpeed welcome message. This message is served over HTTP, not HTTPS.

If you’re using CloudFlare, chances are that CloudFlare will throw a different error because it’s [looking to enforce SSL](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/). Since the default webserver message is being displayed over HTTP, CloudFlare is going to complain about the SSL certificate – which blocks the generic webserver message.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529143712/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
