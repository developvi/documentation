---
title: "Generic Quick Start Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Generic Quick Start Guide
  parent: 01-cloud-deploy-core
  order: 7
---
## Introduction

This quick-start guide is for admin who meet any of the following criteria:

*   Who do not want to use one of our pre-built images on DigitalOcean or AWS.
*   Who are going to be using a server provider other than DigitalOcean
*   Who want to use their own SSH keys instead of letting DVI generate it for them
*   Who are using server providers that do not offer automatic SSH key generation functions

**Note: If you are a first time LICENSED user of DevelopVIDeploy, one of the services we offer is a FREE 1-on-1 walk-through so that you can get up and running fast! We’ll help you install the plugin, configure your ssh keys and get your first server deployed. Just [open a support ticket to request this service](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/submit-ticket/)!**

- - -

## Summary of Steps

If you choose to continue with this quick-start, here are the nine groups of actions you will perform:

1.  Verify your web server meet our requirements.
2.  Upload and activate the plugin to an existing WordPress Site or [deploy a pre-built image at DigitalOcean](https://web.archive.org/web/20240304155058/https://marketplace.digitalocean.com/apps/wpclouddeploy) or [AWS](https://web.archive.org/web/20240304155058/https://aws.amazon.com/marketplace/pp/prodview-bhiab32pkw5ms). We strongly recommend that you use the DigitalOcean or AWS image since it is already pre-configured with all the correct webserver settings.
3.  Setup DVI encryption keys.
4.  Get Your API Keys
5.  Create your SSH Keys
6.  Connect DevelopVIDeploy to your server provider
7.  Fine Tune Your PHP & WEB SERVER Configuration
8.  Install your first server
9.  Install your first site.

- - -

## 1\. Verify Web Server Requirements

Before proceeding with installation, [please read the full requirements here](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/). If the webserver running the website where DVI will be installed does not meet all the requirements (especially the ones for timeouts and firewall/REST API), deploying servers and sites will fail.

- - -

## 2\. Installation and Activation

Installing the plugin is performed just like any other WordPress plugin:

1.  Download the .zip file from our site
2.  Go to the WordPress **Plugins** menu
3.  Click the **Add New** button.
4.  Click the **Upload Plugin** button at the top of the Add Plugins page.
5.  Click the Choose File button, navigate to the .zip file from step 1 and then click the **Install Now** button.
6.  After the upload is complete, click the **Activate** Button.
7.  **_You should now see an alert at the top of the screen indicating the the METABOX.io plugin needs to be installed. You should go ahead and click on the link to install it. Then make sure it gets activated!_**

At this point the plugin is installed and ready to connect to DigitalOcean.

If you will not be connecting to DigitalOcean you should upload one of our premium providers – we support Linode, Vultr, Upcloud, Hetzner, Exoscale, AWS EC2, AWS Lightsail, Google Cloud, Azure and certain private clouds.

Note: Premium providers are only available with a DVI license purchased from our store.

- - -

## 3\. Encryption Keys

Once the plugin is installed and activated you should add an encryption key to your **wp-config.php** file. If you don’t do this now, api keys, private keys and other sensitive data will be stored without encryption in your database. If you add the key later you will have to re-enter your api keys and private key information.

define('WPCD\_ENCRYPTION\_KEY', 'your very long encryption key goes here');

Note: All the possible _wp-config.php_ settings are [documented on this page](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wp-config-entries/).

- - -

## 4\. Obtain Your API Keys For Your Cloud Provider

Each cloud provider has a different method for creating API keys. We have some caveats on keys and other restrictions for certain providers in our [Cloud Provider documentation](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/). Please make sure you read the information for the one(s) you are using before proceeding to the next step.

Also, please make sure you create a read-write keys/tokens – some providers allow you to specify these types of fine-grained permissions.

- - -

## 5\. Create Your SSH Keys

We use SSH keys and only SSH keys to connect to your cloud servers. This means that you must have at least one key-pair created and uploaded to your cloud server providers. OR, for certain providers, we can generate and install them for you.

We can automatically generate and upload SSH keys for the following cloud server providers:

*   DigitalOcean
*   Linode
*   Vultr
*   UpCloud
*   Hetzner
*   OpenStack Private Cloud

Certain other providers have different SSH key requirements. Please make sure you read our [Cloud Provider documentation](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) for your provider(s).

AWS, GOOGLE CLOUD and UPCLOUD in particular have very specific SSH key requirements.

If you need to generate an SSH key-pair, you can [use this guide to learn how to generate one](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/).

_If you going to be using your own SSH keys (either because we don’t offer the option to automatically generate them or because you want to use your own), then it is very important that you create and upload them to your cloud server provider before moving on to the next step!_

- - -

## 6\. Connect To Your Cloud Server Provider

Connecting to your cloud server provider can be very simple or very complex. Simpler providers include DigitalOcean, Linode & Vultr. Complex providers include AWS EC2 & Lightsail, Google Cloud & Azure.

We recommend that you read any of our [Cloud Provider documentation](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) notes for your provider(s).

For this section, we’ll assume you’re using DigitalOcean as your cloud server provider – if you’re using a different provider and have installed and activated the plugin for them, just substitute your provider for DigitalOcean in the instructions below. We’ll insert notes for the more complex providers as well.

1.  Make sure you have made your decision on how to handle your SSH keys – please see the prior section and do not continue until you have figured out your SSH key strategy.
2.  Go to the settings screen under the **DevelopVIDeploy** menu option
3.  Click on the **Cloud Providers** tab and fill out the _API Key_ field then click the save button at the bottom of the screen.
    1.  If you are using AWS EC2, AWS LIGHTSAIL, GOOGLE CLOUD, UPCLOUD or AZURE, please make sure you read our [Cloud Provider documentation](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) – these have very specific setting options that are different from your simpler providers.
4.  If you have uploaded SSH keys to your provider, the SSH key dropdown will be pre-filled with these keys. Select one of them.
5.  If you have uploaded SSH keys to your provider and you do NOT see your keys in the drop-down, you can try one of the following:
    1.  Click the SAVE button again – sometimes you just need to query the cloud provider a second time (some of them perform a sort of micro-caching)
    2.  Use the CLEAR CACHE button at the bottom of settings screen for the provider
    3.  Wait 15 minutes and try again
6.  If you have NOT uploaded SSH keys to your provider and you see a CREATE SSH KEY-PAIR button, you can use that to automatically generate and upload a keypair.
7.  Add the private key portion to the PRIVATE SSH KEY box. It is very very important that you make sure the private key data matches the public key you selected in the prior step. [View important notes about private ssh keys](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/_notes/important-notes-about-private-ssh-keys/).
8.  Add your private key password if any. [View important notes about private ssh keys and passwords](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/_notes/important-notes-about-private-ssh-keys/).
9.  Save the settings.

- - -

## 7\. Fine Tune Your PHP & WEB SERVER Configuration

DVI depends on using SSH to connect to your servers. But the PHP and Web Server processes have short timeouts that need to be increased. It they’re not increased then the amount of time that a connection to one of your managed servers can remain open will be 30 seconds or less – not enough time to handle certain longer running tasks.

We have added instructions to the DevelopVIDeploy->SETTINGS screen to help you increase your timeouts on PHP and various web servers. Please make sure you review these and update your server configurations.

### Firewalls & Proxies

If you place your DVI server / site behind a proxy such as CloudFlare then you need to make sure that the following folders are white-listed so that they can be accessed by your new server:

**/wp-content/plugins/wp-cloud-deploy_/__includes/core/apps/wordpress-app/scripts/v1/raw/_**

This folder just contains just text files in there that happen to contain our bash scripts. These scripts are part of what makes stuff happen – such as installing WordPress on your server.

If you run a firewall plugin on your DVI server you should also make sure the folder is always available to the outside world (or at least every server IP you’re managing).

### Rest Endpoints

You will also need to white-list the call-back endpoints – they all start with or contain _**/wp-json/wordpress-app**._ For this, we would recommend that you whitelist your individual server ip addresses instead of leaving it open.

- - -

## 8\. Create Your First Server

To create your first server:

1.  Go to DevelopVIDeploy → ALL CLOUD SERVERS.
2.  Click the DEPLOY A NEW WORDPRESS SERVER at the top of the screen.
3.  Follow the instructions on the screen and then go get a cup of coffee – it’ll take about 20 minutes for the server to be deployed.

## 9\. Install Your First Site

To create your first site after creating your first server:

1.  Go to DevelopVIDeploy → APPLICATIONS
2.  Click the INSTALL WORDPRESS button in the Server Actions column.
3.  This should be at most a five minute process.

- - -

## Wrap Up

If you run into any issues or errors, check out this [troubleshooting document](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/reasons-servers-fail-to-deploy/) to see if it helps. Otherwise just [contact our tech support team](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/support/) and we’ll jump in to get you all squared away.

And, don’t forget, if you’re a new customer, we will be happy to walk you through this entire process with a 1-on-1 web/screen sharing session. Or, we can perform the installation for free for you. Just ask us and we’ll make an appointment to get it done for you.

- - -

[Go Back To The General Quick Start](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Release Notes](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240304155058/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)


