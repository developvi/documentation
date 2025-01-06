---
title: "Custom Servers (Bring Your Own Server)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Custom Servers (Bring Your Own Server)
  parent: 03-Adminstrator-guide
  order: 24
---
The [Bring Your Own Server](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/downloads/bring-your-own-server/) add-on allow you to use any server at any cloud provider – even if we don’t directly support the provider. You can even use bare-metal servers.

However, the servers must meet our requirements and you might need to exercise a little of your command-line skills in order to initialize the connection to DevelopVIDeploy.

_Note: even though the add-on is named “Bring Your Own Server”, all the screen elements use “Custom Server” as the label for this feature set._

Using a custom server is a three step process:

1.  Prepare your server
2.  Connect your server to DVI
3.  Deploy your server

Here’s a quick video overview:

## Installation

The _Bring Your Own Server_ add-on is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Server Requirements (Preparing Your Server)

Your custom server must meet the following requirements:

*   Have a basic installation of Ubuntu 20.04 LTS or Ubuntu 22.04 LTS (no other software such as nginx, php etc. should be installed.)
*   The “root” user must have an SSH certificate installed and you should be in possession of the related private key.
*   The server must be publicly accessible across the internet and you must know its public IP.
*   It must have its SSH port open (port 22)
*   HTTP and HTTPS ports (80 and 443 respectively) must be opened as well.

The most difficult aspect of these requirements is making sure that the “root” user is configured with an SSH key-pair. If you’re using a cloud-provider such as UpCloud, they can automatically install a key-pair for you (after you’ve uploaded the key-pair to their dashboard). Otherwise you will need to install the key-pair yourself ([this article discusses how to install a public key for your root user.)](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/add-your-existing-ssh-key-to-the-root-user-account/)

Once your server meets these requirements, you can follow the section below to connect it to DVI.

## Connecting The Server To DevelopVIDeploy

A custom server is treated as if it is it’s own cloud service. When you installed the add-on it added a single new cloud provider in the Cloud Settings screen titled “Custom Server”.

*   Go to the DevelopVIDeploy → SETTINGS → CLOUD PROVIDERS tab.
*   Click on the **CUSTOM SERVER** Tab.
*   Enter the _IP_ address of your server.
*   Enter any value into the _AP_I key field
*   Enter the user id of the root user – this is usually “root”.
*   Enter some descriptive text for the region, server size and the SSH key – these take the place of similar data we would normally be pulling from a real cloud service.
*   Click the **SAVE SETTINGS** button.
*   Click the **SAVE SETTINGS** button Again.
*   You should now see the section requesting your **PRIVATE SSH** key for the root user so fill that in.
*   Click the **SAVE SETTINGS** button.

## Deploying Your Custom Server

After following the _Connecting The Server To WPCloudDeploy_ section above, you can finally deploy the server. This is done just like any other server.

*   Go to the DevelopVIDeploy → ALL CLOUD SERVERS.
*   Click the **DEPLOY A NEW WORDPRESS SERVER** button at the top of the screen.
*   In the **PROVIDER** drop-down you should see Custom Server as an option – choose that.
*   Give the server a name.
*   Click the **DEPLOY** button.

As long as the server meets the restrictions set out in the _Server Requirements_ section above, the server should be provisioned just like any other cloud server.

## Deploying Additional Custom Servers

To deploy additional custom servers you need to [create a virtual cloud provider](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/) for each server. _Do not try to reuse or change the data in the CUSTOM SERVER provider that you’ve already used_ – that will break the link to the existing server. Each custom server is treated as if it were a separate and unique cloud provider.

## Notes

*   As you might expect, certain functions that work on real cloud services do not work on custom servers because there is no API available for your custom server. For example, the UPDATE REMOTE STATE link in the server list will always return the server as being active even though you might have powered down the server.
*   Depending on how your server provider configured the default UBUNTU installation, automatic security updates may not be available.

- - -

## Common Errors

### sudo: unable to resolve host

When deploying a custom server, you might see messages such as _sudo: unable to resolve host …._

This is usually because the machine name is not set in the Linux configuration files. Assuming your machine name is something like _ssdnodes-5ff4a61dd6ce4_, you should check the following:

*   That the /etc/hostname file contains just the name of the machine.
*   That /etc/hosts has an entry for localhost. It should have something like:

127.0.0.1 localhost
**127.0.1.1 _ssdnodes-5ff4a61dd6ce4_**

Certain Providers (especially low-end providers) such as **ssdnodes** and **pacificrack** do not set some of these entries so you must add them yourself.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304150410/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
