---
title: "UpCloud Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: UpCloud Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 7
---
## Installing the UpCloud Provider

The UpCloud provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Pre-requisites

### Turn on the API permissions

Under your account screen at UPCLOUD there is a checkbox that enables or disables API permissions. Please make sure that is checked/turned on.

## Configuring the UpCloud Provider

The UpCloud provider needs connection and security information before it can be used.

You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->UpCloud. There are several steps to this process:

*   Enter your UpCloud user name and password.
*   Enter any value for the API key since UpCloud does not use it – but this field should not be empty.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN. This will cause the SSH keys area to show up.
*   Enter the PUBLIC portion and PRIVATE portion of your ssh key pair into the respective fields.
*   Enter the key password if one is used on the key-pair.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN.

## Using the UpCloud Provider

Once the provider has been configured with its connection and API information, it will appear as an option when deploying a new server.

[![](https://web.archive.org/web/20240529155402im_/https://wpclouddeploy.com/wp-content/uploads/2020/09/wpclouddeploy-126.png)](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/wp-content/uploads/2020/09/wpclouddeploy-126.png)

- - -

## Known Issues

### Sensitive Server Names

UpCloud seems unusually sensitive to server names and even the contents of public keys. **Server names must be lower case and server keys cannot contain anything that remotely seems “lewd”**.

### Long Deployment Times

We have noticed that in some regions it will take a long time to deploy servers – as long as 30 minutes. As far as we can tell the first attempt at deploying some packages on the server fails for some odd reason. So the deployment scripts end up waiting a bit and automatically retrying the operation a second time which then succeeds.

### Deleting A Server

It is possible that a server might not be deleted at UpCloud even though it’s been deleted in DVI. This is because the server might take longer to shutdown than the time allowed for executing a single PHP script. **Whenever you delete a server in DVI you should double-check that it has been deleted in UpCloud.** This is probably something you should do with all cloud providers but UpCloud is especially vulnerable to this issue.

Associated with this is the MOVE TO TRASH bulk actions option – if you have an UpCloud server in the list of servers to be deleted you’re likely to have servers remain behind since it is highly probable that the script will timeout. We recommend that, when using the MOVE TO TRASH bulk option on servers, do NOT include your UPCLOUD servers in your selection. Instead, delete your UPCLOUD servers one-by-one.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240529155402/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
