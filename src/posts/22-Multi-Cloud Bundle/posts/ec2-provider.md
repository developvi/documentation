---
title: "EC2 Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: EC2 Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 4
---
## Installing the AWS EC2 Provider

The EC2 provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the AWS EC2 Provider

Connecting to EC2 and automatically creating servers requires a lot more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   EC2 default security groups will block attempts to connect to the server after it’s initially deployed. This needs to be resolved before attempting to deploy your first server (generally by opening it up to incoming traffic on port 22 for IPV4 addresses.)
*   The default firewall will block HTTPS traffic. This needs to be resolved before requesting your first SSL certificate for a site on the server. Please make sure that you do this for IPV4 addresses (EC2 can sometimes default things to only IPV6 addresses).
*   If the default security group and firewall do not already have port 80 open for incoming traffic you should add rules to allow that for IPV4 addresses.
*   You will need to create an IAM user (or use an existing IAM user) with the proper permissions to create EC2 instances. **You will obtain your EC2 ACCESS KEY and EC2 SECRET KEY from this user.**
*   Create or upload an SSH key pair to the region where you will be building your servers. You cannot use the ‘default’ ssh keys that AWS provides – you must create a new pair or upload your own pair. AWS keypairs are specific to a region. If you need to use the same keypair in all regions then you must upload it to all regions. ([How To Create SSH Keys](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/).)

It is very important that all five of the above items be checked and double-checked before proceeding. Otherwise provisioning a server on EC2 WILL FAIL.

## Configuring the AWS EC2 Provider

The AWS EC2 provider then needs connection and security information before it can be used. You can provide this information under WPCLOUD DEPLOY → SETTINGS → CLOUD PROVIDERS → AWS EC2. There are several steps to this process:

*   As mentioned above, make sure you create an SSH Key Pair in your account – you’ll need to do this in the region where you’ll be deploying your servers. Download the private portion of the key. This should be done before performing any of the remaining steps below.
*   Enter the EC2 ACCESS KEY and EC2 SECRET KEY – these are usually defined in the AWS IAM
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

## Using the AWS EC2 Provider

After the provider is installed and configured you’ll see it as an option when deploying a new server:

[![](https://web.archive.org/web/20240529141447im_/https://wpclouddeploy.com/wp-content/uploads/2020/09/wpclouddeploy-120-2.png)](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/wp-content/uploads/2020/09/wpclouddeploy-120-2.png)

- - -

## EC2 Default Security Groups

Servers are placed into EC2’s ‘default’ security group. There are times where this group BLOCKS incoming traffic – this will cause server deployments to fail since we’ll be unable to connect to it automatically. You should EDIT the default security group to ensure that traffic is allowed from your WordPress server where DVI is installed. In particular, the SOURCE for incoming traffic is set to “custom” by default – you need to change this to “Anywhere” or specify the IP address of your WordPress server where DVI is installed.

Alternatively, you can set it up so that only SSH, HTTP and HTTPS traffic are allowed in from all sources.

- - -

## Using Multiple Regions

The basic EC2 provider can only be used in one region. In order to use it in multiple regions, you need to install the [VIRTUAL PROVIDER add-on](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/downloads/virtual-cloud-provider/). Once that has been installed, you can create a virtual provider for each region – learn more in the [Virtual Provider documentation](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/).

If you do not see a region you expect in the region list, please check to make sure that you have opted into that region in your AWS console. AWS now has a nice global view summary that includes a column showing your opt-in status for a region: [https://console.aws.amazon.com/ec2globalview/home#](https://web.archive.org/web/20240529141447/https://console.aws.amazon.com/ec2globalview/home). We have noticed that locations such as Capetown, Milan, Bharain, Hong Kong and Jakarta are usually disabled in new accounts.

You should ensure that there is a default VPC and SECURITY GROUP for each additional region and that they are configured to allow for traffic on certain ports as mentioned in the **Prerequisites For Using the AWS EC2 Provider** section at the top of this page.

- - -

## Default Disk Size

Many EC2 instances default their root device to only **8GB**. For most single WP sites this does not pose an issue. But if you will install multiple sites on the device you will need to increase its size. This exercise requires some comfort level with the command line as well as familiarity with the AWS EC2 console!

*   Step 1 is to log into your EC2 console and use the RESIZE option on the disk for the EC2 instance.
*   Step 2 is to follow the instructions in the EC2 resize documentation: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/recognize-expanded-volume-linux.html](https://web.archive.org/web/20240529141447/https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/recognize-expanded-volume-linux.html)

Step 2 generally involves the use of the _growpart_ and _resize2fs_ commands which:

*   Expands the partition to use all the new space from step 1 and
*   Expands the filesystem to use all the new space added to the partition.

- - -

## IPv6

When you configure the EC2 provider, there is an option to enable IPv6. Before turning this on you must do the following:

*   Assign an IPv6 CIDR to the EC2 default VPC for the region
*   Assign an IPv6 CIDR to the EC2 default SUBNET for the region

If you do not do this, provisioning EC2 instances WILL fail. If you specify an incorrect or invalid IPv6 CIDR for the default VPC and SUBNET provisioning will fail.

- - -

## Using Custom Images

This provider includes support for custom images – i.e.: custom AMIs.

You provide the AMI id in the CUSTOM SNAPSHOTS & IMAGES section of the provider settings area.

Please remember that the AMI must reside in the account and region you’re using. If you need to use the same custom AMI in a different region you will need to copy it to the target region which will give it a different AMI id.

Also, please review these [very important notes about custom images](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/).

- - -

## Known Issues & Limitations

### Backups

Running a backup on an instance that is too small for the amount of data being backed up will cause the MariaDB server to stop. You will have to manually restart it. This seems to be a flaw in the EC2 instance.

So, if you intend to use our backup process on these instances please make sure you run a few backup tests before placing your site into production to make sure there are no issues.

If you do want to continue to use these instances without our backup process in place you can always use a plugin backup process such as Updraft Plus which does not tax the instance as much but takes far longer to complete.

### Server Sync

Server Sync cannot be used on AWS servers – neither as source nor destination.

### Site Sync

The function to copy a site to a new server will not work with AWS EC & Lightsail servers as targets.

### Deleting A Site

When deleting a site, the option to also delete all local backups will not work on AWS servers.

### Missing Regions?

If you’re not seeing a region in the region list dropdown then it’s likely that it has not been enabled for your AWS EC2 account. Many smaller regions are not automatically enabled for most accounts.

- - -

## Gravitron (ARM) Support

This provider includes experimental support for Gravitron instances. Gravitron is the brand name for Amazon’s custom ARM processors.

Depending on your use case, these instances can cost less to run compared to Intel and AMD processors – theoretically, the price/performance ratio is lower.

We have tested basic **NGINX** & **OPENLITESPEED** functionality such as deploying the server, sites and SSL. But have not certified 3rd party software such as MONIT and MALDET. Thus, this is not something you should run in production if you require 3rd party software support; but they might make good development or staging servers if you like playing on the bleeding edge of things.

They’re also great instances to use if all you are doing is creating sites that use just the basic WP functions without any of the advanced DVI features. i.e.:

*   Install Site
*   Enable/Disable SSL
*   Enable/Disable CACHE
*   Backup/Restore
*   Site Tweaks
*   etc.

Almost anything that only uses PHP should work but anything that requires a binary (most 3rd party software) have not been certified.

- - -

## Resources

Want to know which EC2 instance to use? Take a look at [this document on Github](https://web.archive.org/web/20240529141447/https://github.com/wrble/public/blob/main/aws-instance-types.md) that outlines all the various instance types and their differences.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240529141447/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
