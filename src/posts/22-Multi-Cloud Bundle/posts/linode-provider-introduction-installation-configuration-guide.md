---
title: "Linode Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Linode Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 6
---
## Installing the LINODE Provider

The LINODE provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Configuring the LINODE Provider

The LINODE provider, as with other providers, need connection and security information before it can be used.

You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->Linode. There are several steps to this process:

*   **_Make sure you upload an SSH Keypair to your LINODE dashboard. You should do this before performing any other steps!_**
*   Enter your LINODE user name
*   Enter your LINODE API Key – you can get this key from the API section of your [LINODE dashboard](https://web.archive.org/web/20240529154945/https://cloud.linode.com/profile/tokens). (Create a PERSONAL token with READ/WRITE privileges.)
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN. This will cause the SSH keys area to show up.
*   Select one of the SSH keys from the drop-down.
*   Enter the PRIVATE portion of the ssh key pair into the _Private SSH Key_ field.
*   Enter the key password if one is used on the key-pair.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN.

- - -

## Notes

Some Linode datacenters randomly refuse to complete our start up scripts – in these cases you’ll see output such as the following:

Adding additional repositories
Failed! Quitting process

If this continues to occur, you should choose a different data center or retry your preferred data center later.

### Linode Names

When setting a name for your server, the following rules must be followed (taken from the Linode API guide)

*   Must start with an alpha character.
*   May only consist of alphanumeric characters, dashes (-), underscores (\_) or periods (.).
*   Cannot have two dashes (–), underscores (\_\_) or periods (..) in a row.

### SSH Keys

Linode automatically installs all public keys for the designated user name into new Linodes. So, if there are any “test” keys in your account, you should remove them before creating Linodes or use a different user name configured with only your production SSH keys.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240529154945/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
