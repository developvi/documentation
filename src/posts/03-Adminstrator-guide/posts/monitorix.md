---
title: "Monitorix"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Monitorix
  parent: 03-Adminstrator-guide
  order: 25
---
Monitorix is a utility that provides some nice semi-realtime charts showing detailed statistical activity on your server.

## Activate MONITORIX

*   Go to DevelopVIDeploy->All Cloud Servers
*   Click on the server for which this action will apply
*   Click on the _MONITORIX_ tab
*   Specify a domain, user id and password. Make sure you configure your DNS to point the domain to your server IP.
*   Click the _Install Monitorix_ button
*   Click the _OK_ option on the confirmation popup

If all goes well, Monitorix will be installed and the screen will refresh.

_Next, you should use the SSL option on the MONITORIX tab to install an SSL certificate. Otherwise, your user id and password for your Monitorix dashboard will be sent over the internet without any protection or encryption._

## Launch MONITORIX

*   Install Monitorix as described in the Activate MONITORIX section above
*   Go to DevelopVIDeploy->All Cloud Servers
*   Click on the server for which this action will apply
*   Click on the _MONITORIX_ tab
*   Click the _Launch Monitorix_ button. Sometimes this will not open the site so you might have to manually navigate to the url and then enter the user id and password.

## Notes

1.  When installing on a Multisite you cannot use a subdomain of the multisite domain as your Monitorix domain. For example, if your main multisite domain is _mymultisitedomain.com,_ you cannot use _monitorix.mymultisitedomain.com_ as your domain for Monitorix. This is because WordPress is in control of all subdomains on a Multisite so an http request for _monitorix.mymultisitedomain.com_ will never make it to the Monitorix site. Instead, you should use another subdomain of a domain that is not a multisite domain residing on the server.
2.  Monitorix is NOT an available option on servers using the OpenLiteSpeed webserver.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [File Manager](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529151800/https://wpclouddeploytation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
