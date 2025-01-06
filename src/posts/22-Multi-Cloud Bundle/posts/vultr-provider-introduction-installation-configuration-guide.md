---
title: "Vultr Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Vultr Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 9
---
## Introduction

The DevelopVIDeploy VULTR provider is actually three providers in one. It has providers for VULTR’s V1 API (which they have deprecated) as well as providers for their newer V2 API and Bare Metal Servers.

When you install the provider you will see options for both V2 and Bare Metal only; but you can turn on an option to see the V1 provider if you need that for your use case.

## Prerequisites

*   VULTR blocks all API requests by default. You need to allow your servers IP address access to the VULTR API – you can do this on the [VULTR dashboard](https://web.archive.org/web/20240420010633/https://my.vultr.com/settings/#settingsapi).
*   DVI timeouts need to be increased to 40 minutes. You can do this in the TIMEOUT FOR LONG RUNNING COMMANDS section on the DevelopVIDeploy → SETTINGS → MISC tab

## Installing the VULTR Provider

The VULTR provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Configuring the VULTR Provider

The VULTR provider, as with other providers, need connection and security information before it can be used.

You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->Vultr. There are several steps to this process:

*   **_Make sure you upload an SSH Keypair to your VULTR dashboard. You should do this before performing any other steps!_**
*   Enter your VULTR API Key – you can get this key from the API section of your [VULTR dashboard](https://web.archive.org/web/20240420010633/https://my.vultr.com/settings/#settingsapi).
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN. This will cause the SSH keys area to show up.
*   Select one of the SSH keys from the drop-down.
*   Enter the PRIVATE portion of the ssh key pair into the _Private SSH Key_ field.
*   Enter the key password if one is used on the key-pair.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN.

## Notes

*   VULTR wants to restrict api access by IP. If it seems like the provider not working properly, check to make sure that the [VULTR API does not have an IP restriction in effect](https://web.archive.org/web/20240420010633/https://my.vultr.com/settings/#settingsapi). Or, if it does, make sure that it is set to the IP of the WordPress server running DVI.
*   Additionally, if your server has an IPV6 address, you might need to white-list that address as well. If whitelisting just the IPV4 address does not work then you should whitelist the IPV6 addresses as well.
*   VULTR is notorious for not having their HF server sizes available everywhere – and we don’t get that information via the API. So, you have to look on their site first and figure out what’s available and where. Then provision that combination in the DVI dashboard. Most other providers are similar but they usually try to not be as bad at it as VULTR is.
*   VULTR servers take a long time to be deployed – as much as 45 minutes. This is because their API does not mark the server as being up-and-running until all VULTR background tasks have been completed.

## Bare Metal Notes

*   VULTR frequently runs out of their bare metal servers; so you should check to make sure that they’re available in the region you’re interested in before attempting to deploy using DVI. Otherwise, the deploy will fail. We do show region availability in the size drop-down but sometimes even the API is wrong. So you should always check their website first.

[![](https://web.archive.org/web/20240420010633im_/https://wpclouddeploy.com/wp-content/uploads/2021/08/wpcd-v4-148.png)](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/wp-content/uploads/2021/08/wpcd-v4-148.png)

You can read more about this provider in [our latest VULTR release article](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/significant-updates-to-our-vultr-provider/).

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240420010633/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
