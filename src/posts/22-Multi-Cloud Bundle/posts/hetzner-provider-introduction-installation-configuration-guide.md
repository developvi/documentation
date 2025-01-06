---
title: "Hetzner Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Hetzner Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 8
---
## Installing the Hetzner Provider

The Hetzner provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Configuring the Hetzner Provider

The Hetzner provider needs connection and security information before it can be used.

You can provide this information under **DevelopVIDeploy** → **SETTINGS** → **CLOUD PROVIDERS** → **Hetzner**. There are several steps to this process:

*   Enter your API key – you can obtain this from your HETZNER CLOUD dashboard. API keys are unique to each Hetzner project.
*   Click the **SAVE** button
*   Click the **SAVE** button AGAIN. This will cause the SSH keys area to show up.
*   Enter the PUBLIC portion and PRIVATE portion of your ssh key pair into the respective fields.
*   Enter the key password if one is used on the key-pair.
*   Click the **SAVE** button
*   Click the **SAVE** button AGAIN.

## Using the HETZNER Provider

Once the provider has been configured with its connection and API information, it will appear as an option when deploying a new server.

[![](https://web.archive.org/web/20240529153040im_/https://wpclouddeploy.com/wp-content/uploads/2023/06/wpcd-hetzner-01.png)](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/wp-content/uploads/2023/06/wpcd-hetzner-01.png)

- - -

## ARM Processor Support

This provider includes experimental support for ARM instances. Depending on your use case, these instances can cost less to run compared to Intel and AMD processors – theoretically, the price/performance ratio is lower.

[![](https://web.archive.org/web/20240529153040im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-50-hetzner-arm-experimental-support-deploy-server-02.png)](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-50-hetzner-arm-experimental-support-deploy-server-02.png)

We have tested basic **NGINX** and **OPENLITESPEED** functionality such as deploying the server, sites and SSL. But we have not certified 3rd party software such as MONIT and MALDET. Thus, this is not something you should run in production if you require 3rd party software support; but they might make good development or staging servers if you like playing on the bleeding edge of things.

They’re also great instances to use if all you are doing is creating sites that use just the basic WP functions without any of the advanced DVI features. i.e.:

*   Install Site
*   Enable/Disable SSL
*   Enable/Disable CACHE
*   Backup/Restore
*   Site Tweaks
*   etc.

Almost anything that only uses PHP should work but anything that requires a binary (most 3rd party software) have not been certified.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240529153040/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
