---
title: "Using Our DigitalOcean Template Image"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Using Our DigitalOcean Template Image
  parent: 07-Others-&-Misc
  order: 1
---
## Introduction

We have prebuilt a server image on the DigitalOcean marketplace that you can use to quickly deploy a server & site with DevelopVIDeploy already pre-installed.

You will need some basic SSH skills to be able to log into the server and follow the prompts so you can connect your domain and setup DVI.

[Launch DVI Droplet At Digital Ocean](https://web.archive.org/web/20240529153557/https://marketplace.digitalocean.com/apps/wpclouddeploy)

After navigating to the DigitalOcean droplet page with the above button, please click the **CREATE WpCloudDeploy  DROPLET** button to get the DVI image started.

When the droplet has been created you will need to **login to it via SSH to continue the setup process.**

When you login for the first time you will be asked to choose your domain and to provide your email address. Your email address is required to setup your SSL certificate and to make sure that your DVI site knows where to send any alerts.

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-do-template-first-login-01.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-do-template-first-login-01.png)

If the domain you provide is pointed to the IP address of the new droplet we’ll request an SSL certificate. _We strongly recommend that you point your domain IP address to the new droplet PRIOR to entering the domain name here so that the SSL certificate can be issued_.

When you get to the end of the process you will see additional instructions on how to access the site.

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-do-template-first-login-02.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-do-template-first-login-02.png)

Generally your site can be accessed at **https://yourdomain.com/wp-admin**.

- - -

## (Optional) Remove The Start up Script

**In some versions of the DigitalOcean image**, if you log out and log back into the server using SSH, you will be prompted to setup the site again. This is because the setup script is part of the root user after-login script.

If you proceed to run through the setup again, you will irreversibly damage the original site. Instead you should CTRL-BREAK / CTRL-C out of the script.

To prevent the script from accidentally running again you can remove the script from the root user start up sequence as follows:

Edit the root user start up script:

nano ~/.bashrc

Scroll down to the bottom of the file. There you will see a line that looks like this:

bash /root/800\_do\_first\_login.sh

Just delete the line (and the related comment above it). Then save the file:

ctrl-o <enter>

And exit the nano editor:

ctrl-x

Test that the script no longer runs on login by logging out and then logging back in with ssh.

- - -

## Upgrade To Latest Plugin Version \[Premium License\]

If you’ve purchased a license from us, it is possible that you have a more recent version of the plugin than what is on the droplet. So the first thing you should do is upload a copy of the version of the plugin you got from us – you can do this from the regular WordPress PLUGINS screen.

**Premium Providers**

Additionally, if your license include premium providers such as Linode and Vultr, you should upload those and activate them as well. This will allow you to use the quick-start Wizard (described later) with these premium providers.

- - -

## Setup Options

Once you’re logged into DVI for the first time, you have a number of ways to proceed with setup.

*   **Easy Setup** – you can use this method if you will be deploying WordPress servers on DigitalOcean, Linode, Vultr, Upcloud or Hetzner AND you will allow DVI to automatically create SSH key-pairs for you (and upload them to your Cloud Provider’s account). You cannot use this method if you’ll be deploying servers at other cloud server providers such AWS or Azure.
*   **Advanced Setup** – You will need to use this option if you want to deploy WordPress servers at any provider other than DigitalOcean, Linode, Vultr, Upcloud and Hetzner; OR you want to use your own SSH key-pairs.

- - -

## Using DevelopVIDeploy For The First Time: Easy Setup

When you log into DevelopVIDeploy for the first time you will see a green banner at the top of the screen. This will allow you to invoke an easy on-boarding process as long as you are deploying your new servers into the DigitalOcean, Linode, Vultr, Upcloud or Hetzner cloud.

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-01.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-01.png)

If for some reason you are not deploying servers to DigitalOcean, Linode, Vultr, Upcloud or Hetzner and you have one of our other premium providers (eg: AWS, Azure, etc.), you MUST skip this on-boarding process and use the advanced instructions shown later in this document.

To continue with this easy setup, click the button in the green banner to get started and you’ll see the first page of the on-boarding wizard.

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-02.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-02.png)

Because we have automatically created an encryption key for you with this droplet you can just click the green CONTINUE button to move to the next step:

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-03.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-03.png)

You can get your API Key from your Cloud Provider’s dashboard – use the API Menu option to generate a key. Make sure the key has WRITE permissions!

Enter the api key and click the green CONTINUE button to move to the next step where you will generate your SSH key-pair:

[![](https://web.archive.org/web/20240529153557im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-04.png)](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-wizard-04.png)

We use SSH keys instead of passwords to access your servers. This step will allow us to generate a unique pair for you, submit the public portion to your Cloud Provider and securely store the private portion in DVI.

Just click the green CONTINUE button to proceed.

At the next step click the green CONTINUE button to complete the process and go to the servers list.

- - -

### 1\. Create Your First Server

To create your first server:

1.  Go to WpCloudDeploy  → CLOUD SERVERS.
2.  Click the DEPLOY A NEW WORDPRESS SERVER at the top of the screen.
3.  Follow the instructions on the screen and then go get a cup of coffee – it’ll take about 20 minutes for the server to be deployed.

Important: Please choose a server size with at least 1 GB RAM. DigitalOcean offers droplets with as little as 512MB but those will not work for DVI WordPress servers.

After a server is provisioned you will be returned to the servers list where you will see the new server available for use. _You will also see a message in the health column about CALLBACKS being unavailable – you can ignore that message because they will eventually be installed in the background._

### 2\. Install Your First Site

To create your first site after creating your first server:

1.  Go to WpCloudDeploy  → CLOUD SERVERS
2.  Click the INSTALL WORDPRESS button in the Server Actions column. This should take no more than 5 minutes to complete.
3.  Update your DNS for the new site/domain to point to the server.

- - -

- - -

## Using DevelopVIDeploy For The First Time: Advanced Setup

As mentioned earlier in this document, you will need to use this option if you want to deploy WordPress servers at any provider other than DigitalOcean OR you want to use your own SSH key-pairs.

## Summary of Steps

1.  (Optional) Upload and activate premium plugins
2.  Get DigitalOcean API Key (or API keys for your preferred cloud server provider)
3.  Create your SSH Keys
4.  Connect WpCloudDeploy  To DigitalOcean (or your preferred cloud server provider)
5.  Install your first server
6.  Install your first site.

- - -

### 1\. (Optional) Installation and Activation (Premium Plugins)

The Core DevelopVIDeploy plugin is already installed and ready to be connected to a DigitalOcean account.

However, if you’re going to be connecting to any other cloud provider (eg: Linode, AWS etc.), then you must purchase a license from our [store](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/pricing/) and download the premium provider plugins from your account.

Installing any premium provider plugin is performed just like any other WordPress plugin:

1.  Download the .zip file from our site
2.  Go to the WordPress **Plugins** menu
3.  Click the **Add New** button.
4.  Click the **Upload Plugin** button at the top of the Add Plugins page.
5.  Click the Choose File button, navigate to the .zip file from step 1 and then click the **Install Now** button.
6.  After the upload is complete, click the **Activate** Button.

- - -

### 2a. Create A DigitalOcean API Key

Create an API key at Digital Ocean – you can do this inside your DigitalOcean dashboard.

Use the API menu option on the left side of the screen after you login to your account.

Please make sure you create a read-write key/token.

### 2b. Create API Keys For Your Preferred Cloud Server Provider

If you are not going to be use DigitalOcean to deploy your WordPress servers then you must obtain API keys for whichever service you will be using.

Each cloud provider has a different method for creating API keys. We have some caveats on keys and other restrictions for certain providers in our [Cloud Provider documentation](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/). Please make sure you read the information for the one(s) you are using before proceeding to the next step.

Also, please make sure you create a read-write keys/tokens – some providers allow you to specify these types of fine-grained permissions.

- - -

### 3\. Create Your SSH Keys

We use SSH keys and only SSH keys to connect to your cloud servers. This means that you must have at least one key-pair created and uploaded to your cloud server providers. OR, for certain providers, we can generate and install them for you.

We can automatically generate and upload SSH keys for the following cloud server providers:

*   DigitalOcean
*   Linode
*   Vultr
*   UpCloud
*   Hetzner
*   OpenStack Private Cloud

Certain other providers have different SSH key requirements. Please make sure you read our [Cloud Provider documentation](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) for your provider(s).

AWS, GOOGLE CLOUD and UPCLOUD in particular have very specific SSH key requirements.

If you need to generate an SSH key-pair, you can [use this guide to learn how to generate one](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/).

_If you going to be using your own SSH keys (either because we don’t offer the option to automatically generate them or because you want to use your own), then it is very important that you create and upload them to your cloud server provider before moving on to the next step!_

- - -

### 4\. Connect To Your Cloud Provider

Connecting to your cloud server provider can be very simple or very complex. Simpler providers include DigitalOcean, Linode & Vultr. Complex providers include AWS EC2 & Lightsail, Google Cloud & Azure.

We recommend that you read any of our [Cloud Provider documentation](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) notes for your provider(s).

For this section, we’ll assume you’re using DigitalOcean as your cloud server provider – if you’re using a different provider and have installed and activated the plugin for them, just substitute your provider for DigitalOcean in the instructions below. We’ll insert notes for the more complex providers as well.

1.  Make sure you have made your decision on how to handle your SSH keys – please see the prior section and do not continue until you have figured out your SSH key strategy.
2.  Go to the settings screen under the **DevelopVIDeploy** menu option
3.  Click on the **Cloud Providers** tab and fill out the _API Key_ field then click the save button at the bottom of the screen.
    1.  If you are using AWS EC2, AWS LIGHTSAIL, GOOGLE CLOUD, UPCLOUD or AZURE, please make sure you read our [Cloud Provider documentation](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/) – these have very specific setting options that are different from your simpler providers.
4.  If you have uploaded SSH keys to your provider, the SSH key dropdown will be pre-filled with these keys. Select one of them.
5.  If you have uploaded SSH keys to your provider and you do NOT see your keys in the drop-down, you can try one of the following:
    1.  Click the SAVE button again – sometimes you just need to query the cloud provider a second time (some of them perform a sort of micro-caching)
    2.  Use the CLEAR CACHE button at the bottom of settings screen for the provider
    3.  Wait 15 minutes and try again.
6.  If you have NOT uploaded SSH keys to your provider and you see a CREATE SSH KEY-PAIR button, you can use that to automatically generate and upload a keypair.
7.  Add the private key portion to the PRIVATE SSH KEY box. It is very very important that you make sure the private key data matches the public key you selected in the prior step. [View important notes about private ssh keys](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/_notes/important-notes-about-private-ssh-keys/).
8.  Add your private key password if any. [View important notes about private ssh keys and passwords](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/_notes/important-notes-about-private-ssh-keys/).
9.  Save the settings.

Now you’re ready to quickly run through the steps to get your first server and site up and running.

- - -

### 5\. Create Your First Server

To create your first server:

1.  Go to WpCloudDeploy  → CLOUD SERVERS.
2.  Click the DEPLOY A NEW WORDPRESS SERVER at the top of the screen.
3.  Follow the instructions on the screen and then go get a cup of coffee – it’ll take about 20 minutes for the server to be deployed.

Important: Please choose a server size with at least 1 GB RAM. Your provider might offer instances with as little as 512MB but those will not work for DVI WordPress servers.

### 6\. Install Your First Site

To create your first site after creating your first server:

1.  Go to WpCloudDeploy  → CLOUD SERVERS
2.  Click the INSTALL WORDPRESS button in the Server Actions column. This should take no more than 5 minutes to complete.
3.  Update your DNS for the new site/domain to point to the server.

- - -

## Wrap Up

If you run into any issues or errors, check out this [troubleshooting document](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/wpcloud-deploy/reasons-servers-fail-to-deploy/) to see if it helps. Otherwise just [contact our tech support team](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/support/) and we’ll jump in to get you all squared away.

And, don’t forget, if you’re a new customer, we will be happy to walk you through this entire process with a 1-on-1 web/screen sharing session. Or, we can perform the installation for free for you. Just ask us and we’ll make an appointment to get it done for you.

- - -

[Go Back To The General Quick Start](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)

- - -

### More Topics In Other & Misc

*   [Using Our AWS EC2 Core Template](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-template-image/)
*   [AWS EC2 Premium Template](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-premium-template-image/)
*   [Translations](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/translations/)
*   [Moving The DVI Plugin To A New Server](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/moving-the-wpcd-plugin-to-a-new-server/)
*   [Simultaneous Dashboard Actions](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/simultaneous-dashboard-actions/)
*   [White Label](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/white-labelling/)
*   [Command, SSH & Error Logs](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/command-ssh-error-logs/)
*   [Server Groups](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/server-groups/)
*   [Application (Site) Groups](https://web.archive.org/web/20240529153557/https://wpclouddeploy.com/documentation/other-misc/application-site-groups/)
