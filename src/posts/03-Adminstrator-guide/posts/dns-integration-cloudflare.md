---
title: "DNS Integration CloudFlare"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: DNS Integration CloudFlare
  parent: 03-Adminstrator-guide
  order: 18
---
DevelopVIDeploy includes a simple integration with CloudFlare that enable the following features:

*   Automatically create temporary domains and register them with the CloudFlare DNS service
*   Automatically delete the temporary domain when the site is deleted
*   Automatically issue SSL certificates with LetsEncrypt for temporary domains registered with CloudFlare

To set this up:

*   Go to **WpCloudDeploy** → **SETTINGS** → **APP: WordPress Settings** → DNS **INTEGRATION: CLOUDFLARE**
*   Enter the root of your temporary domain (eg: temp.com) – this MUST be registered on Cloudflare and can be a maximum of 19 characters including the extension. You cannot use a subdomain such as temp.mydomain.com.
*   Click the **ENABLE CLOUDFLARE AUTO DNS** checkbox
*   Obtain your Zone ID for the domain from your CloudFlare dashboard and enter it into the **ZONE ID** field. The Zone ID is usually on the bottom right of the summary screen for your domain.
*   Get an **API SECURITY TOKEN** from your CloudFlare account and enter it into the **API SECURITY TOKEN** field – make sure this token has access to the domain! (See more detailed instructions in a later section if you need help with this.)
*   Turn on the options for **AUTO DELETE, AUTO SSL** and **CLOUDFLARE PROXY** as needed.
*   Click the **SAVE SETTINGS** button.

Now, when you create a new WordPress site, a temporary domain will automatically be entered into the DOMAIN field.

[![](https://web.archive.org/web/20240304144512im_/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-v4-069.png)](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-v4-069.png)

- - -

## How To Get A CloudFlare Token

Navigate to the Cloudflare Token screen for your account – it’s generally located at this URL: [https://dash.cloudflare.com/profile/api-tokens](https://web.archive.org/web/20240304144512/https://dash.cloudflare.com/profile/api-tokens)

1.  Click _Create Token_
2.  Use the template for _Edit zone DNS_
3.  Under _Zone Resources_, select your domain
4.  Click _Continue_ to Summary
5.  Click _Create Token_

You should be shown your token. You should copy and save it into a password manager since CF will not show it to you again. Then copy it to the appropriate locations in DVI.

- - -

## Notes

*   If you have a high volume of sites being created every week and you turn on AUTO SSL, you might run into SSL limits with LetsEncrypt – you can only issue 50 certificates for a domain in a 7 day period. Learn more on the [LetsEncrypt Limits Page](https://web.archive.org/web/20240304144512/https://letsencrypt.org/docs/rate-limits/#:~:text=If%20you%20have%20a%20lot,5%2C000%20unique%20subdomains%20per%20week.).
*   Having problems with issuing SSL certificates? This might help: [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   If you need to use a custom SSL certificate, read the [command line Custom SSL Certificate documentation](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/).
*   You can use a separate CloudFlare domain for your WooCommerce integration – see the [Setup Cloudflare DNS Integration section on the WooCommerce Integration pages](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/) for more information.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [Site Packages](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304144512/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
