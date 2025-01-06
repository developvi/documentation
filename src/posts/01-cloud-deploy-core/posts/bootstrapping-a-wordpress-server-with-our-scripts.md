---
title: "Bootstrapping A WordPress Server With Our Scripts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Bootstrapping A WordPress Server With Our Scripts
  parent: 01-cloud-deploy-core
  order: 17
---


Note: These instructions apply to developvideploy  5.0 or later. If you need instructions for version 4.x please [view this link](https://web.archive.org/web/20231001082813/https://wpclouddeploy .com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/).

- - -

## Introduction

Using the developvideploy  plugin presents a chicken-and-egg problem since it requires an existing WordPress installation in order to work. Most users will have one of these already and might be able to configure it to meet our [requirements](https://web.archive.org/web/20231001082813/https://wpclouddeploy .com/wpcloud-deploy-requirements/). If you don’t then you can:

*   Deploy a pre-built image at DigitalOcean using this link: [https://marketplace.digitalocean.com/apps/wpclouddeploy .](https://web.archive.org/web/20231001082813/https://marketplace.digitalocean.com/apps/wpclouddeploy ) This is the simplest option if you’re going to build the server yourself.
*   If you’re not a fan of DigitalOcean you can deploy a pre-built image at Amazon instead using this link: [https://aws.amazon.com/marketplace/pp/prodview-bhiab32pkw5ms](https://web.archive.org/web/20231001082813/https://aws.amazon.com/marketplace/pp/prodview-bhiab32pkw5ms)
*   Fireup a basic DigitalOcean instance where WP is already installed and configured for you ([DigitalOcean](https://web.archive.org/web/20231001082813/https://www.digitalocean.com/community/tutorials/how-to-use-the-wordpress-one-click-install-on-digitalocean-2), [Linode](https://web.archive.org/web/20231001082813/https://www.digitalocean.com/community/tutorials/how-to-use-the-wordpress-one-click-install-on-digitalocean-2), [Vultr](https://web.archive.org/web/20231001082813/https://www.vultr.com/docs/one-click-wordpress/))
*   Opt to use our free install service where we’ll install it for you on a server of your choice (as long as it meets the dvi requirements) – just request the service via a support ticket within 30 days of your license purchase and we’ll get right on it for you. **This is our preferred option if you want to use your own custom server. We really really want to do this for you so you can get up and running FAST!**

After WordPress is up and running, you can just install dvi by following our [Quick Start instructions](https://web.archive.org/web/20231001082813/https://wpclouddeploy .com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/).

**While we prefer that you use our free installation service** or one of the prebuilt images at [DigitalOcean](https://web.archive.org/web/20231001082813/https://marketplace.digitalocean.com/apps/wpclouddeploy ) or [AWS](https://web.archive.org/web/20231001082813/https://aws.amazon.com/marketplace/pp/prodview-bhiab32pkw5ms), if you really Really REALLY want to start from scratch and do it yourself, you can use our scripts to bootstrap the initial server – you just have to be willing to get down into the command line.

## Bootstrapping A WordPress Server With Our Scripts

Here is how it works (These are the same steps we follow when you request our free install service.)

1.  Decide where you’re going to host your server. We recommend that you host it in a location away from where the majority of your other servers will be located. So, if you plan on using DigitalOcean for most of your servers then this bootstrapped server might be located at Linode or Vultr or AWS.
2.  Fireup a standard (not minimal) 20.04 UBUNTU server with no additional software installed on it.
3.  Log into the server and make sure that the dos2unix package is installed. You can do this by running the following commands in sequence
    1.  sudo apt-get update -yqm

    2.  sudo apt-get install -yqm dos2unix

4.  Upload the following scripts to the server from the plugin’s _includes/core/apps/wordpress-app/scripts/v1/raw folder._ We use a product called [Termius](https://web.archive.org/web/20231001082813/https://termius.com/) to connect to the server and upload the files using drag-and-drop. You can also use free tools such as [BitVise.](https://web.archive.org/web/20231001082813/https://www.bitvise.com/download-area) or, of course, any other tool you like. The goal is to get these scripts up to a known folder on the server:
    1.  1.  1.  01-prepare\_server.txt

            2.  02-install\_wordpress\_site.txt

            3.  04-manage\_https.txt

            4.  10-misc.txt

            5.  9999-common-functions.txt

            6.  6G-Firewall-OLS

            7.  7G-Firewall-OLS

5.  Navigate to the folder where you uploaded the scripts and run the following command. These ensure that the txt files have the correct line endings for linux:
    1.  sudo dos2unix \*.txt

6.  Rename one of the files to have the correct extension:
    1.  mv 9999-common-functions.txt 9999-common-functions.sh

7.  While inside the folder where the scripts exist, execute each of the first three scripts in sequence and follow the on screen instructions. (Before running the https script, make sure you have updated your DNS to point your domain to the server’s ip address)
    1.  1.  sudo bash ./01-prepare\_server.txt

        2.  sudo bash ./02-install\_wordpress\_site.txt

        3.  sudo bash ./04-manage\_https.txt

8.  At this point you have should have a working site with SSL enabled. Now you need to make sure that WP-CRON is going to get fired every 1 min. So execute the following command:

    sudo bash ./10-misc.txt

9.  Choose option **13** from the large list of menu options. The WP-CRON will be configured to fire every 60 seconds and you should be back at the command line.

Now, lets proceed to tweak a few of the web server settings.

## Server Configuration Tweaks

We need to modify your site to increase script and web server timeout values.

Edit your new site’s configuration file:

nano /etc/nginx/sites-enabled/your-domain-name

Add the _max\_execution\_time=300;_ entry to it as shown in this image (notice that the line ends with a semi-colon):

[![12.07.2020-23.40](https://web.archive.org/web/20231001082813im_/https://content.screencast.com/users/StructuredMarketsInc/folders/wpclouddeploy /media/b56aa2a2-03fa-4ab7-a52d-76c7ffa6cd1a/12.07.2020-23.png?source=oembed)](https://web.archive.org/web/20231001082813/https://www.screencast.com/t/qLV0pQVnMOra)

Under the line that starts with _client\_max\_body\_size_, add the following entries:

fastcgi\_read\_timeout 600;
client\_header\_timeout 600;
client\_body\_timeout  600;

[![12.07.2020-23.42](https://web.archive.org/web/20231001082813im_/https://content.screencast.com/users/StructuredMarketsInc/folders/wpclouddeploy /media/84002a45-e398-48ab-b01a-b62c9ed01355/12.07.2020-23.png?source=oembed)](https://web.archive.org/web/20231001082813/https://www.screencast.com/t/LmH1Iof1HU)

Restart the web server:

service nginx restart

## Next Steps

*   [Setup the dvi Better Crons](https://web.archive.org/web/20231001082813/https://wpclouddeploy .com/documentation/wpcloud-deploy/better-wpcd-crons/)
*   [Install and configure the wpclouddeploy  Plugin](https://web.archive.org/web/20231001082813/https://wpclouddeploy .com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

## Optional

*   Run the _18-wp\_cache.txt_ script to enable caching. This is recommended if your site will be used by customers.
*   Run the _23-fail2ban.txt_ script to install fail2ban. Be careful since you can easily lock yourself out of your server if you don’t know what you’re doing here.
*   Run the _37-backup-configuration.txt_ script . This will backup the dvi configuration periodically to a different folder.
*   Run the _08-backups.txt_ script to setup daily backups to AWS S3.
*   Run the _12-redis.txt_ script to add REDIS (recommended if you’re going to be using WooCommerce on the dvi site).


