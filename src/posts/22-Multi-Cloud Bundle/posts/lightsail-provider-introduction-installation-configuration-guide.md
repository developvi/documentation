---
title: "Lightsail Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Lightsail Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 12
---
## Installing the AWS Lightsail Provider

The Lightsail provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the AWS Lightsail Provider

Connecting to Lightsail and automatically creating servers requires a lot more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   You will need to create an IAM user (or use an existing IAM user) with the proper permissions to create Lightsail instances. **You will obtain your Lightsail ACCESS KEY and Lightsail SECRET KEY from this user.**
*   Create or upload an SSH key pair to the region where you will be building your servers. You cannot use the ‘default’ ssh keys that AWS provides – you must create a new pair or upload your own pair. AWS keypairs are specific to a region. If you need to use the same keypair in all regions then you must upload it to all regions. ([How To Create SSH Keys](https://web.archive.org/web/20240304151810/https://developvideploy.com/documentation/how-to-generate-an-ssh-key-pair/).)

It is very important that all of the above items be checked and double-checked before proceeding. Otherwise provisioning a server on AWS Lightsail WILL FAIL.

## Configuring the AWS Lightsail Provider

The AWS Lightsail provider then needs connection and security information before it can be used. You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->AWS LIGHTSAIL. There are several steps to this process:

*   As mentioned above, make sure you create an SSH Key Pair in your account – you’ll need to do this in the region where you’ll be deploying your servers. Download the private portion of the key. This should be done before performing any of the remaining steps below.
*   Enter the AWS ACCESS KEY and AWS SECRET KEY – these are usually defined in the AWS IAM
*   Click the SAVE button
*   Click the SAVE button AGAIN. This will cause the REGION drop-down to be populated from data in your AWS account
*   Select a region from the REGION drop-down
*   Click the SAVE button
*   Click the SAVE button AGAIN
*   Click the CLEAR CACHE button at the bottom of the screen to force a cache refresh of your keys list. This will cause the PUBLIC SSH keys drop-down to be populated from data in your AWS account.
*   Select a key from the PUBLIC SSH KEY drop-down. _Be careful – this drop-down is initially populated with keys from your account’s default region. If you’re using a different region, you should make sure that the list shown here is the one for your selected region. You might have to save the screen a couple of times to force it to refresh._
*   Enter your private key that correspond to the public key
*   Click the SAVE button
*   Click the SAVE button AGAIN.

## Using the AWS Lightsail Provider

After the provider is installed and configured you’ll see it as an option when deploying a new server:

[![](https://web.archive.org/web/20240304151810im_/https://developvideploy.com/wp-content/uploads/2022/03/wpcd-v4-256.png)](https://web.archive.org/web/20240304151810/https://developvideploy.com/wp-content/uploads/2022/03/wpcd-v4-256.png)

After a server is deployed you MUST enable HTTPS using the AWS Lightsail console. Otherwise you will not be able to access your sites over HTTPS.

To do this, login to your AWS Lightsail console and click on the server. Then access the networking tab for the server and add the HTTPS port for both IPv4 and IPv6.

- - -

## Using Multiple Regions

The basic Lightsail provider can only be used in one region. In order to use it in multiple regions, you need to install the [VIRTUAL PROVIDER add-on](https://web.archive.org/web/20240304151810/https://developvideploy.com/downloads/virtual-cloud-provider/). Once that has been installed, you can create a virtual provider for each region – learn more in the [Virtual Provider documentation](https://web.archive.org/web/20240304151810/https://developvideploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/).

- - -

## Known Issues & Limitations

### Backups

Running a backup on an instance that is too small for the amount of data being backed up will cause the MariaDB server to stop. You will have to manually restart it. This seems to be a flaw in the Lightsail instance.

So, if you intend to use our backup process on these instances please make sure you run a few backup tests before placing your site into production to make sure there are no issues.

If you do want to continue to use these instances without our backup process in place you can always use a plugin backup process such as Updraft Plus which does not tax the instance as much but takes far longer to complete.

### Server Sync

Server Sync cannot be used on AWS servers – neither as source nor destination.

### Site Sync

The function to copy a site to a new server will not work with AWS EC & Lightsail servers as targets.

### Deleting A Site

When deleting a site, the option to also delete all local backups will not work on AWS servers.

- - -

## Issues With Specific Regions

### Mumbai

There have been reports from customers of issues with deploying Lightsail servers in the Mumbai region. Sometimes servers seem to require a reboot or are just unstable and need to be recreated.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240304151810/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
