---
title: "Alibaba ECS Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Alibaba ECS Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 2
---
## Installing the Alibaba ECS Provider

The Alibaba ECS provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the Alibaba ECS Provider

Connecting to Alibaba ECS and automatically creating servers requires a lot more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   You must create a user with the appropriate permissions in the Alibaba RAM console (see more information close to the bottom of this document)

## Configuring the Alibaba ECS Provider

First, you must make sure you create an SSH key pair to the region where you will be building your servers. Each region will need their own key-pair.

The Alibaba ECS provider then needs connection and security information before it can be used. You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->ALIBABA. There are several steps to this process:

*   As mentioned above, make sure you create an SSH Key Pair in your account – you’ll need to do this in the region where you’ll be deploying your servers. Download the private portion of the key. This should be done before performing any of the remaining steps below.
*   Also, as mentioned above, you will need to create a RAM user with the appropriate permissions for ECS.
*   Enter the RAM user’s ACCESS KEY and SECRET KEY – these are usually defined in the Alibaba RAM (Resource Access Management) console.
*   Click the SAVE button
*   Click the SAVE button AGAIN. This will cause the REGION drop-downs to be populated from data in your Alibaba ECS account.
*   Select a region from the REGION drop-down
*   Click the SAVE button
*   Click the SAVE button AGAIN.
*   Click the CLEAR CACHE button at the bottom of the screen to force a cache refresh of your keys list. This will cause the PUBLIC SSH keys drop-downs to be populated from data in your Alibaba ECS account.
*   Select a key from the PUBLIC SSH KEY drop-down. Note: If you do not see the PUBLIC SSH keys then click the CLEAR CACHE button at the bottom.
*   Enter your private key that correspond to the public key
*   Click the SAVE button
*   Click the SAVE button again.

## Using the Alibaba ECS Provider

After the provider is installed and configured you’ll see it as an option when deploying a new server:

[![](https://web.archive.org/web/20240304143138im_/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpcd-v4-031.png)](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpcd-v4-031.png)

## User Permissions

Before you can create servers, you must create a user with the appropriate permissions in the Alibaba RAM (Resource Access Management) console.

The RAM User needs the following permissions:

*   AliyunECSFullAccess
*   AliyunVPCFullAccess

Grant users permissions in the RAM console here: https://ram.console.aliyun.com/users

This is also where you’ll create users and assign them an access key and secret key. Once the user is created, you can assign them the required permissions as listed above.

## Server Defaults

Servers that are created from inside DVI will always be deployed with the following options:

*   Deployed to the first zone in the specified region
*   Will create a new VPC, Vswitch & Security Group
*   Will **NOT** delete the VPC, Vswitch & Security Groups when the server is deleted. You must delete these from the Alibaba cloud dashboard.

As a result, if you create a lot of servers, you will likely exceed your VPC limits. So make sure you request an increase in those limits!

If you do not like these defaults you have three options:

1.  Deploy the servers as custom servers
2.  Create a new provider that uses your defaults – you can copy our existing provider plugin, change it and deploy it under a new plugin name.
3.  Modify the provider plugin code directly to change the defaults (not recommended).

## Using Multiple Regions

The basic Alibaba ECS provider can only be used in one region. In order to use it in multiple regions, you need to install the [VIRTUAL PROVIDER add-on](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/downloads/virtual-cloud-provider/). Once that has been installed, you can create a virtual provider for each region – learn more in the [Virtual Provider documentation](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/).

## Compatibility Notes

In some cases this provider cannot be run in conjunction with Amazon EC2 and Amazon Lightsail. If you encounter this issue you must turn off the Amazon providers before enabling this one.

## Limitations

### Server Sync

Server Sync cannot be used on AWS servers – neither as source nor destination.

### Site Sync

The function to copy a site to a new server will not work with this provider.

### Deleting A Site

When deleting a site, the option to also delete all local backups will not work with this provider.

## Known Issues

*   Servers cannot be reliably created in China Mainland datacenters – we have seen an almost 100% failure rate there. As best we can tell, some of the repositories we use as the source for packages are blocked – in particular wp-cli. However, datacenters outside of Mainland china seem to be fine. To use servers in mainland China you might need to modify our BASH scripts to pull packages from an unblocked repository.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240304143138/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
