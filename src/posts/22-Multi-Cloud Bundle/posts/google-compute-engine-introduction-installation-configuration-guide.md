---
title: "Google Compute Engine Introduction, Installation & Configuration Guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Google Compute Engine Introduction, Installation & Configuration Guide
  parent: Multi-Cloud Bundle
  order: 10
---
## Installing the Google Compute Platform (GCP) Provider

The Google Compute Platform provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the GCP Provider

Connecting to GCP and automatically creating servers requires a lot more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   You need to create a service account inside your project and download the service account JSON credentials file. You can do this under IAM & ADMIN → SERVICE ACCOUNTS in the GCP console. The service accounts must have roles and rights to create/modify/delete VMS and related components (including manipulating the firewall). The JSON file can be downloaded from the KEYS tab under the service account you created.

## Configuring the GCP Provider

Unlike most other providers, you’ll need to configure both the public key and private key inside our settings screen. **For GCP, the public and private keys have very very specific requirements**.

*   As mentioned above you’ll need an SSH Keypair (both parts – public and private)
*   The public key can only be the the public key text – the preamble such as ‘ssh-rsa’ and any trailing text such as a user name or email address must be removed.
*   The private key has the same rules.
*   The keypair must be an RSA keypair.
*   Also as mentioned above you’ll need the GCP JSON service account credentials file – make sure that it has the rights to create VM’s in the project.

On the SETTINGS screen (under DevelopVIDeploy → SETTINGS → CLOUD PROVIDERS → GOOGLE):

*   Enter your PROJECT ID
*   Enter the contents of the Service Account JSON file
*   Click the SAVE button
*   Click the SAVE button AGAIN – this will reveal the rest of the settings screen.
*   Enter the PUBLIC KEY from your SSH key-pair
*   Choose a REGION
*   Enter the PRIVATE KEY from your SSH key-pair
*   Enter a password for the SSH private key (if any)
*   Click the SAVE button
*   Click the SAVE button again.

## Using Multiple Regions And Multiple GCP Projects

The basic GCP provider can only be used in one region and one project. In order to use it in multiple regions, you need to install the [VIRTUAL PROVIDER add-on](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/downloads/virtual-cloud-provider/). Once that has been installed, you can create a virtual provider for each region & project combination – learn more in the [Virtual Provider documentation](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/).

- - -

## Compatibility Notes

*   In some cases this provider cannot be run in conjunction with Alibaba, Amazon EC2 and Amazon Lightsail. This is because these providers all have APIs that use the same libraries – but different versions of those libraries which can sometimes conflict with each other. If you encounter this issue you must turn off the other providers before enabling this one. If you need to use these other providers as well you can create a new DVI instance and use them there.

- - -

## Limitations

### Server Sync

Server Sync cannot be used on GCP servers – neither as source nor destination.

### Site Sync

The function to copy a site to a new server will not work with this provider.

### Deleting A Site

When deleting a site, the option to also delete all local backups will not work with this provider.

- - -

## Known Issues

*   Server provisioning will sometimes randomly fail with a “Failed Quitting Process” message. In this case you should delete the server from the DVI dashboard and restart the process. While all providers sometimes have incidents where the servers fail to deploy properly, GCP seems to have a much much higher failure rate – higher than everyone else except maybe DigitalOcean. _Note that this means that if you allow GCP servers with WooCommerce, you might have to keep a close eye on those servers during the provisioning process after an order is placed!_
*   We have noticed that sometimes the GCP VMs randomly stop responding until you manually restart them from the GCP dashboard. This seems to happen if you reboot the instance too many times in a short period of time. There might be other actions that cause this behavior as well. A key indicator that you are encountering this behavior is that you cannot SSH into the VM – you get a “connection refused” or similar message. Once you restart from the GCP console you are able to SSH into the server again and everything else starts to work properly again.

- - -

## Other Notes

### Server Names

GCP requires your server names to be unique. So, we will be adding a random 5 character string to the end of every server name you specify to avoid inadvertent duplicates. For example, if you try to create a server with the name “MYNEWSERVER” we will convert it into something like “MYNEWSERVER-axytz”.

### Default Disk Size

All servers, regardless of number of CPUs, will be provisioned with 50 GB of disk space.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240529143552/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
