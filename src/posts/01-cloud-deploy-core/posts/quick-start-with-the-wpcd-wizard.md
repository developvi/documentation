---
title: "Quick Start With The DVI Wizard"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Quick Start With The DVI Wizard
  parent: 01-cloud-deploy-core
  order: 4
---
# Quick Start With The DVI Wizard

## Introduction

This quick-start guide is appropriate for users who meet the following criteria:

*   Will use DigitalOcean, Linode, Vultr, UpCloud or Hetzner as a server provider and
*   Will allow DVI to generate SSH keys (instead of using your own)

If you do not meet these two criteria you can choose on of the following options:

[Go Back To The General Quick Start](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

[Use our Generic Quick Start Guide](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)

- - -

## Summary of Steps

If you choose to continue with this quick-start, here are the seven groups of actions you will perform:

1.  Verify your web server meet our requirements.
2.  Upload and activate the plugin to an existing WordPress Site.
3.  Setup DVI encryption keys.
4.  Get an API Key from your Cloud Provider
5.  Connect DevelopVIDeploy to your Cloud Provider
6.  Fine Tune Your PHP & WEB SERVER Configuration
7.  Install your first server
8.  Install your first site.

- - -

## 1\. Verify Web Server Requirements

Before proceeding with installation, [please read the full requirements here](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/). If the webserver running the website where DVI will be installed does not meet all the requirements (especially the ones for timeouts and firewall/REST API), deploying servers and sites will fail.

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

**Optional: Install Premium Providers**

If you have a license for one or more of our premium Cloud providers you should upload those plugins as well and activate them. The onboarding wizard will work with the following premium providers if they are activated:

*   Linode
*   Vultr
*   UpCloud
*   Hetzner

At this point the plugin(s) are installed and ready to connect to your Cloud Provider.

But first though, you should add an encryption key to wp-config.php.

- - -

## 3\. Encryption Keys

Once the plugin is installed and activated you should add an encryption key to your **wp-config.php** file. If you don’t do this now, api keys, private keys and other sensitive data will be stored without encryption in your database. If you add the key later you will have to re-enter your api keys and private key information.

define('WPCD\_ENCRYPTION\_KEY', 'your very long encryption key goes here');

Note: All the possible _wp-config.php_ settings are [documented on this page](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wp-config-entries/).

- - -

## 4\. Create An API Key At Your Cloud Provider

Create an API key at your cloud provider (DigitalOcean, Linode etc.) You can do this inside your Cloud Provider’s dashboard.

For DigitalOcean, use the API menu option on the left side of the screen after you login to your account.

Please make sure you create a read-write key/token.

- - -

## 5\. Connect DVI To DigitalOcean (Or Linode/Vultr/UpCloud/Hetzner) Using the DVI Onboarding Wizard

When you log into DevelopVIDeploy for the first time you will see a green banner at the top of the screen. This will allow you to invoke an easy on-boarding process as long as you are deploying your new servers into the DigitalOcean (or Linode/Vultr/UpCloud/Hetzner) cloud.

[![](https://web.archive.org/web/20240420014655im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-01.png)](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-01.png)

If for some reason you are not deploying servers to DigitalOcean (or Linode/Vultr/UpCloud/Hetzner) and you have one of our other premium providers (eg: AWS, Azure, etc.), you should use our generic quick start guide:

[Use our Generic Quick Start Guide](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)

Otherwise, click the button in the green banner to get started and you’ll see the first page of the on-boarding wizard.

[![](https://web.archive.org/web/20240420014655im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-02.png)](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-02.png)

Because you should have already added an encryption key you can just click the green CONTINUE button to move to the next step:

[![](https://web.archive.org/web/20240420014655im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-03.png)](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-03.png)

As mentioned earlier, you can get your API Key from your Cloud Provider’s dashboard – use the API Menu option to generate a key. Make sure the key has WRITE permissions!

Enter the api key and click the green CONTINUE button to move to the next step where you will generate your SSH key-pair:

[![](https://web.archive.org/web/20240420014655im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-04.png)](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-04.png)

We use SSH keys instead of passwords to access your servers. This step will allow us to generate a unique pair for you, submit the public portion to your cloud provider and securely store the private portion in DVI.

Just click the green CONTINUE button to proceed.

At the next step click the green CONTINUE button to complete the process and go to the servers list.

- - -

## 6\. Fine Tune Your PHP & WEB SERVER Configuration

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

## 7\. Create Your First Server

To create your first server:

1.  Go to DevelopVIDeploy->CLOUD SERVERS.
2.  Click the DEPLOY A NEW WORDPRESS SERVER at the top of the screen.
3.  Follow the instructions on the screen and then go get a cup of coffee – it’ll take about 20 minutes for the server to be deployed.

Important: Please choose a server size with at least 1 GB RAM. DigitalOcean offers droplets with as little as 512MB but those will not work for DVI WordPress servers.

After a server is provisioned you will be returned to the servers list where you will see the new server available for use. _You will also see a message in the health column about CALLBACKS being unavailable – you can ignore that message because they will eventually be installed in the background._

## 8\. Install Your First Site

To create your first site after creating your first server:

1.  Go to DevelopVIDeploy->CLOUD SERVERS
2.  Click the INSTALL WORDPRESS button in the Server Actions column. This should be at most a five minute process.
3.  Update your DNS for the new site/domain to point to the server.

- - -

[Go Back To The General Quick Start](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240420014655/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)

- - -
