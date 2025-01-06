---
title: "DigitalOcean Provider Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: DigitalOcean Provider Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 3
---
## Installing the DigitalOcean Provider

The DigitalOcean provider is built into the core plugin so no installation is necessary.

## Configuring the DigitalOcean Provider

Before you can start to use DigitalOcean cloud servers you need to tell DVI how to talk to them.

You can provide this information in the DevelopVIDeploy → SETTINGS → CLOUD PROVIDERS → DigitalOcean tab. There are several steps to this process:

*   **_Make sure you upload the public portion of an SSH Keypair to your DigitalOcean dashboard. Or you can use the CREATE SSH KEY-PAIR button to automatically generate a pair for you. Either way you should make sure there is an SSH public key in your DigitalOcean account before performing any other steps!_**
*   Enter your DigitalOcean API Key – you can get this key from the API section of your [DigitalOcean dashboard](https://web.archive.org/web/20240420011630/https://cloud.digitalocean.com/account/api/tokens).
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN. This will cause the SSH keys area to show up.
*   Select one of the public SSH keys from the drop-down.
*   Enter the PRIVATE portion of the ssh key pair into the _Private SSH Key_ field. This private portion must be the one that is associated with the public key you selected above.
*   Enter the key password if one is used on the keypair.
*   Click the SAVE BUTTON
*   Click the SAVE BUTTON AGAIN.

At this point your DigitalOcean provider should be configured. All other information is optional.

## Notes

Recently we’ve noticed that smaller servers fail to deploy properly at DigitalOcean. You will see one of two error messages in the “terminal” when a server fails to deploy:

*   **sudo: dos2unix: command not found.** – This one is usually followed by this message: _Unfortunately the server provisioning process has failed. Please delete this server and restart! Sorry about that!_
*   **Failed – quitting process** – This one shows up after attempting to add and configure additional repositories.

In general you just have to delete the server from our server list and then retry the deployment. Sometimes choosing a different location helps and sometimes just choosing a different size will succeed.

Depending on the time of day, we might have to try 3 or 4 times to get a server to deploy all the way.

Our best guess for this is that, during deployment we are hammering at the server since we’re installing a ton of software packages. So any virtual server that is slightly unstable will be prone to fail sooner rather than later. Many of DigitalOcean’s data centers are close to capacity and it is possible that some new small servers are simply being provisioned on machines that are already crowded. Choosing a different size or location will generally cause the new VM to be attempted on a different physical machine.

The upside is that servers that deploy fully will be far more stable and less likely to suffer a VM failure in the future.

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240420011630/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
