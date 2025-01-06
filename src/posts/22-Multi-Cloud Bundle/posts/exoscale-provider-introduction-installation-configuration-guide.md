---
title: "Exoscale Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Exoscale Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 5
---
## Installing the Exoscale Provider

The Exoscale provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the Exoscale Provider

Connecting to Exoscale and automatically creating servers requires a few more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   Before attempting to provision a server you must update your default security group to open ports 22, 80 and 443 (ssh, http and https).

## Configuring the Exoscale Provider

First, you must make sure you create and upload an SSH key pair to your Exoscale dashboard.

The Exoscale provider then needs connection and security information before it can be used. You can provide this information in the WPCLOUD DEPLOY → SETTINGS → CLOUD PROVIDERS → Exoscale tab. There are several steps to this process:

*   As mentioned above, you must make sure you edit your default security group in the Exoscale console to open ports 22, 80 and 443.
*   Create an API key-pair in your Exoscale console (generally under ACCOUNT → API ACCESS)
*   Enter the SECRET KEY and the API KEY into our settings screen.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN. This will cause the PUBLIC SSH keys drop-downs to be populated from data in your Exoscale account
*   Select a key from the PUBLIC SSH KEY drop-down
*   Enter your private key that correspond to the public key
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON again.

## Server Defaults

Servers that are created from inside DVI will always be deployed with the following options:

*   Security Group: Default

Because we are using the default security group, you MUST make sure that you edit it to open ports 22, 80 and 443 BEFORE you attempt to provision a server inside DVI. These rules should look similar to the following:

[![](https://web.archive.org/web/20240304134843im_/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpcd-v4-032.png)](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpcd-v4-032.png)

## Notes

All servers will be provisioned with 50GB of disk space, regardless of server size.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploywpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240304134843/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
