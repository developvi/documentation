---
title: "Using Post-Processing Custom Bash Scripts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Using Post-Processing Custom Bash Scripts
  parent: 03-Adminstrator-guide
  order: 40
---
## Introduction

Up until this feature was introduced in DVI 4.16.2, you could only make use of your custom bash scripts either by:

*   Modifying the existing scripts directly or
*   Writing a full add-on to insert them using DVI hooks and filters.

With this feature you now have a third option for the most common use case – running commands at the end of the server provisioning and site provisioning processes.

There are two types of post-processing scripts.

1.  Remote scripts
2.  Local Scripts

- - -

## Remote Post-processing Scripts

These scripts are used for new sites and servers. Because these servers and sites do not yet exist, there’s no place ‘local’ to store them so we allow you to set them up remotely.

## Set Up

First you need a place where you can create a **publicly accessible text file** using a **standard https url**. For example, the RAW version of gists.

Create a file with the bash commands you need to run.

Then, set the link in the DevelopVIDeploy → SETTINGS → APP:WORDPRESS → CUSTOM SCRIPTS tab.

[![](https://web.archive.org/web/20240304153213im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-v4-269.png)](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-v4-269.png)

## What Can You Do With This?

You can create simple text files and make them available at a public link with bash commands.

For new servers, you can:

*   Disable or enable server processes
*   Install new server components
*   Reboot the server
*   Reboot the server and then install or run new scripts

For new sites you can do the following:

*   Use WP-CLI to install plugins and themes from WordPress.org on new sites
*   Insert or update constants into the wp-config.php file (eg: memory limit) in new sites
*   Modify the amount of PHP memory used in the PHP processes for new sites or servers
*   Increase or decrease the number of PHP workers used in new sites or servers

Your scripts will have access to the full complement of variables – which means that there is a lot of you can do without having to customize DVI code directly. The above are just some ideas.

## Example

Here is an example of a post-processing script you can use on a site to install two plugins from the wordpress.org plugin repository:

View the code on [Gist](https://web.archive.org/web/20240304153213/https://gist.github.com/elindydotcom/980f91e2f260e6dbefa817770c8ea744.js).

## Using Secret Keys

So, you have a situation where you need to access a private github repository or maybe you want to add your plugin license key to new site installs. Since you should not place private data into public scripts, you need to make use of a secrets manager. The one we’ve used is called doppler.com but you can use any you like, as long as the following two requirements are met:

1.  It only requires a single API token instead of a key/value pair and
2.  It has an api can you can use from your bash script.

You can enter your api token in the SECRETS MANAGER API KEY field (see image earlier in this document). Then, that value will be available in the bash environment variable: **$secret\_key\_manager\_api\_key**

With this key, you should then be able to pull in all your other keys directly from your secrets manager.

## Using Secret Gists

You can use a secret GIST for your post-processing scripts. There are two caveats to be aware of:

1.  You must use the url for the RAW gist. Otherwise you’ll end up attempting to execute some odd combination of embedded JS and HTML script.
2.  If you change your gist, the URL changes! So you will need to keep updating the settings in the DevelopVIDeploy -> SETTINGS -> APP:WORDPRESS -> CUSTOM SCRIPTS tab if you make frequent changes to your script.

## Notes

There are, of course some things to watch out for when using this feature:

*   These scripts have to be publicly accessible. But they can be ‘secret’ links such as the raw links to secret gists.
*   Because they must be publicly accessible you cannot (or should not) include any private information such as api keys.

From a security perspective, if your remote link is compromised, so will any new servers or sites you provision.

Additionally, this feature is only useful if you do not need to set state data using post-metas in the DVI plugin. Scripts you run using this method have no way of writing data back to DVI without a custom add-on.

- - -

## Local Post-processing Scripts

Some operations allow you to create a script with a specific name in an existing site or server. When the operation is complete it will look for a script with a particular name and run it if it exists.

The list of operations and the expected script name are as follows:

*   Cloning Sites: _wpcd\_clone\_site\_after\_clone\_script.sh_

The post-processing script for cloning is especially useful when cloning ‘template’ sites associated with Multi-tenancy or our WooCommerce Integration. Add the script to the root of your template site and it will be executed after the site is cloned.

- - -

## Other

Need post-processing scripts for other functions? Let us know your use case and we’ll try out best to make it happen!

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304153213/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
