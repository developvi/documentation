---
title: "Changing SSH Keys For A Cloud Provider"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Changing SSH Keys For A Cloud Provider
  parent: Multi-Cloud Bundle
  order: 15
---
When DVI wants to connect to a server it looks in the DVI SETTINGS screen, under the CLOUD PROVIDERS tab, to get the login information. It usually needs the private portion of the SSH keypair for the server in order to login but with some providers it might also need the name of the sudo user.

If you change the private key or public key in that screen, then ALL new AND existing servers will start to use the new private key information.

For existing servers, this can be an issue unless you update their root/sudo user with the new public key. If you have a lot of servers, this can be a lot of work. So, unless you have a security issue that require you to change your keys, that’s probably not the best approach.

There is an alternative – you can provide private key information on a server-by-server basis while utilizing the key information in the SETTINGS → CLOUD PROVIDERS tab for all other servers.

[![](https://web.archive.org/web/20240529151434im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-060.png)](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-060.png)

This means that, depending on what you need, you can either:

1.  Change the PUBLIC and PRIVATE ssh keypair in the DVI SETTINGS → CLOUD PROVIDERS tab which will apply to all new servers. Then update the private key information in the server KEYS tab for all existing servers. Or…
2.  Add the PRIVATE ssh key for one or more servers under the servers’ KEYS tab for a select few servers. Servers that are not updated that way will continue to use the data under the DVI SETTINGS → CLOUD PROVIDERS tab to login.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Custom Images](https://web.archive.org/web/20240529151434/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
