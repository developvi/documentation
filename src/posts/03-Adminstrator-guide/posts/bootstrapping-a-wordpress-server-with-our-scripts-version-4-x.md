---
title: "Bootstrapping A WordPress Server With Our Scripts – Archive Version 4.x"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Bootstrapping A WordPress Server With Our Scripts – Archive Version 4.x
  parent: 03-Adminstrator-guide
  order: 44
---
#### NOTE: This document covers an older version of DevelopVIDeploy.

#### [Click here to view the instructions for the most recent version here instead](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/).

- - -

Using the DevelopVIDeploy plugin presents a chicken-and-egg problem since it requires an existing WordPress installation in order to work. Most users will have one of these already and might be able to configure it to meet our [requirements](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/wpcloud-deploy-requirements/). If you don’t then you can:

* Deploy a pre-built image at DigitalOcean using this link: [https://marketplace.digitalocean.com/apps/wpclouddeploy.](https://web.archive.org/web/20240529154832/https://marketplace.digitalocean.com/apps/wpclouddeploy) This is the simplest option if you’re going to build the server yourself.
* Fireup a basic DigitalOcean instance where WP is already installed and configured for you ([DigitalOcean](https://web.archive.org/web/20240529154832/https://www.digitalocean.com/community/tutorials/how-to-use-the-wordpress-one-click-install-on-digitalocean-2), [Linode](https://web.archive.org/web/20240529154832/https://www.digitalocean.com/community/tutorials/how-to-use-the-wordpress-one-click-install-on-digitalocean-2), [Vultr](https://web.archive.org/web/20240529154832/https://www.vultr.com/docs/one-click-wordpress/))
* Opt to use our free install service where we’ll install it for you on a server of your choice (as long as it meets the DVI requirements) – just request the service via a support ticket within 30 days of your license purchase and we’ll get right on it for you. **This is our preferred option if you want to use your own custom server. We really really want to do this for you so you can get up and running FAST!**

After WordPress is up and running, you can just install DVI by following our [Quick Start instructions](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/).

**While we prefer that you use our free installation service** or the [pre-built DigitalOcean image](https://web.archive.org/web/20240529154832/https://marketplace.digitalocean.com/apps/wpclouddeploy), if you really Really REALLY want to start from scratch and do it yourself, you can use our scripts to bootstrap the initial server – you just have to be willing to get down into the command line.

Here is how it works (These are the same steps we follow when you request our free install service.)

1.  Decide where you’re going to host your server. We recommend that you host it in a location away from where the majority of your other servers will be located. So, if you plan on using DigitalOcean for most of your servers then this bootstrapped server might be located at Linode or Vultr or AWS
2.  Fireup a standard (not minimal) 20.04 UBUNTU server with no additional software installed on it.
3.  Log into the server and make sure that the dos2unix package is installed. You can do this by running the following commands in sequence
  1.  sudo apt-get update -yqm

  2.  sudo apt-get install -yqm dos2unix

4.  Upload the following scripts to the server from the plugin’s _includes/core/apps/wordpress-app/scripts/v1/raw folder._ We use a product called [Termius](https://web.archive.org/web/20240529154832/https://termius.com/) to connect to the server and upload the files using drag-and-drop. You can also use free tools such as [BitVise.](https://web.archive.org/web/20240529154832/https://www.bitvise.com/download-area) or, of course, any other tool you like. The goal is to get these scripts up to a known folder on the server:
  1.
    1. prepare\_server.txt

    2.  02-install\_wordpress\_site.txt

    3.  04-manage\_https.txt

    4.  10-misc.txt

5.  Navigate to the folder where you uploaded the scripts and run the following command. These ensure that the txt files have the correct line endings for linux:
  1.  sudo dos2unix \*.txt

6.  While inside the folder where the scripts exist, execute each of the scripts in sequence and follow the on screen instructions. (Before running the https script, make sure you have updated your DNS to point your domain to the server’s ip address)
  1.  sudo bash ./01-prepare\_server.txt

  2.  sudo bash ./02-install\_wordpress\_site.txt

  3.  sudo bash ./04-manage\_https.txt

7.  At this point you have should have a working site with SSL enabled. Now you need to make sure that WP-CRON is going to get fired every 1 min. So execute the following command:

  sudo bash ./10-misc.txt

8.  Choose option **13** from the large list of menu options. The WP-CRON will be configured to fire every 60 seconds and you should be back at the command line.

Now, lets proceed to tweak a few of the web server settings.

## Server Configuration Tweaks

We need to modify your site to increase script and web server timeout values.

Edit your new site’s configuration file:

nano /etc/nginx/sites-enabled/your-domain-name

Add the _max\_execution\_time=300;_ entry to it as shown in this image (notice that the line ends with a semi-colon):

[![12.07.2020-23.40](https://web.archive.org/web/20240529154832im_/https://content.screencast.com/users/StructuredMarketsInc/folders/wpclouddeploy/media/b56aa2a2-03fa-4ab7-a52d-76c7ffa6cd1a/12.07.2020-23.png?source=oembed)](https://web.archive.org/web/20240529154832/https://www.screencast.com/t/qLV0pQVnMOra)

Under the line that starts with _client\_max\_body\_size_, add the following entries:

* fastcgi\_read\_timeout 600;

* client\_header\_timeout 600;

* client\_body\_timeout  600;


[![12.07.2020-23.42](https://web.archive.org/web/20240529154832im_/https://content.screencast.com/users/StructuredMarketsInc/folders/wpclouddeploy/media/84002a45-e398-48ab-b01a-b62c9ed01355/12.07.2020-23.png?source=oembed)](https://web.archive.org/web/20240529154832/https://www.screencast.com/t/LmH1Iof1HU)

Restart the web server:

* service nginx restart


## Next Steps

* [Install and configure the DevelopVIDeploy Plugin](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

## Optional

* Run the _23-fail2ban.txt_ script to install fail2ban
* Run the _37-backup-configuration.txt_ script to backup the DVI configuration periodically to a different folder.
* Run the _08-backups.txt_ script to setup daily backups AWS S3.
* Run the _12-redis.txt_ script to add REDIS (recommended if you’re going to be using WooCommerce on the DVI site).

### More Topics In Admin

* [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
* [Backups With AWS S3](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
* [Restoring From Backup](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
* [6G Firewall (Deprecated)](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
* [7G Firewall](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
* [Native Linux Cron](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
* [Disabling Sites](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
* [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
* [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
* [Remove/Delete Site](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
* [Manage PHP Options](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
* [Add A WordPress Administrator](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
* [Notifications and Alerts](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
* [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
* [Object Cache: MemCached](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
* [Object Cache: Redis](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
* [Monit / Healing](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
* [DNS Integration: CloudFlare](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
* [Site Packages](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
* [Site Update Plans](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
* [Site Expiration](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
* [White Label Colors](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
* [Adding Custom NGINX Configs](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
* [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
* [How To Change The IP Address For Your Server](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
* [Virtual Cloud Providers](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
* [Monitorix](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
* [File Manager](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
* [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
* [Using Remote Databases](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
* [SMTP Gateway](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
* [Server Updates](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
* [Theme & Plugin Updates](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
* [Bulk Actions on Servers](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
* [Bulk Actions on Sites](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
* [SSH Key Overrides](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
* [Webserver Types](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
* [DVI Cron Jobs](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
* [Disk Quotas](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
* [Custom Post Type Quotas](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
* [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
* [Bulk Copy To Server](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
* [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
* [Shortcodes](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
* [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
* [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529154832/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
