---
title: "One-click Login (AKA Passwordless Logins)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: One-click Login (AKA Passwordless Logins)
  parent: 03-Adminstrator-guide
  order: 8
---
If you’re an administrator you’ll see an option in the site list that allow you to login to the site without entering a user name or password.

[![](https://web.archive.org/web/20240304144724im_/https://wpclouddeployent/uploads/2024/02/wpcd-57-passwordless-login-magic-login-01.png)](https://web.archive.org/web/20240304144724/https://wpclouddeployent/uploads/2024/02/wpcd-57-passwordless-login-magic-login-01.png)

You will also see a similar login link for at the top of the SITE DETAILS screen:

[![](https://web.archive.org/web/20240304144724im_/https://wpclouddeployent/uploads/2024/02/wpcd-57-passwordless-login-magic-login-02.png)](https://web.archive.org/web/20240304144724/https://wpclouddeployent/uploads/2024/02/wpcd-57-passwordless-login-magic-login-02.png)

- - -

## Login as Any User

The login links described above will search the site users and login as the first administrator account it encounters. However, there are times where you might want to login as a particular user. In this case you can do so under the site **USERS** tab.

[![](https://web.archive.org/web/20240304144724im_/https://wpclouddeployent/uploads/2024/02/wpcd-v57-passwordless-login-link-02.png)](https://web.archive.org/web/20240304144724/https://wpclouddeployent/uploads/2024/02/wpcd-v57-passwordless-login-link-02.png)

This function is particularly useful if you are troubleshooting an issue that only presents for a particular user or user role. With it, you no longer need to take the separate step of adding a user-switching plugin to the site.

- - -

## Disabling The Login Links

You can remove the passwordless login links with an option in the settings area:

*   Go to **WpCloudDeploy** → **SETTINGS** → **APP: WORDPRESS** – **SETTINGS** → **SITES**
*   Scroll down to the **MISC** section
*   Turn on the _DISABLE THE ONE-CLICK LOGIN BUTTONS_ option.
*   Click the **SAVE SETTINGS** button.

If you like you can delete the **WP CLI Login Command Server** plugin before you log out of the site. If you need to use the one-click login function again for that site it will be automatically installed.

- - -

## Notes

Here are some things to keep in mind about how that works:

1.  The first time you use a passwordless login link it will take about 30 seconds to connect to the server, install the dependencies and inject the login plugin into the site. This is important to understand because it adds a plugin to the site.
2.  The next time you use the link it will take 10 – 15 seconds to connect to the server, get the one-time login token and redirect to it.
3.  The site will open in a NEW browser tab – because of this, **you might have to approve pop-ups before you see the site**.
4.  If you have multiple users in the Administrator group, you will be logged in as one of them. No admin users are ever added to your site.
5.  If you have removed the Administrator role for some reason, you will not be able to use this function (though you can customize the script to pick a different role or force it to always use the same user id, email address or user name.)
6.  Only wpcd administrators will see this login option.

- - -

## Troubleshooting

### Check your PHP CLI Version

You can check the SSH logs (**WpCloudDeploy → SSH Logs**) to see if WP-CLI is throwing errors. If it is you might want to make sure that your WordPress plugins and themes for the site is compatible with the version of the PHP CLI active on the server.

Take a look at the **WpCloudDeploy → TOOLS** screen ( SET SERVER PHP CLI VERSION section) to see what version of the server PHP CLI is currently active.

If the site is currently running, say PHP 7.4 but the server PHP CLI Is set to 8.1, it is possible that an error could be thrown because WP CLI is trying to run some PHP 7.4 plugin / theme code from the site under the server’s PHP 8.1 CLI.

The solution is to make sure that the server PHP CLI version is set to the same version as the site (or, at least a more compatible version).

- - -

## Known Issues

*   If you use a 2FA plugin for your site administrators, this function will not work at all.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304144724/https://wpclouddeploytation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
