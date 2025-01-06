---
title: "Custom Images"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Custom Images
  parent: Multi-Cloud Bundle
  order: 16
---
Some providers allow you to use custom images in place of the default OS image.

This is a double-edged sword.

## The Good

Using a custom image can dramatically decrease the time it takes to deploy a server. It depends on what you pre-install on it of course.

## The Bad

If you use a custom image, it is only valid for one DVI version and one web server type.

In other words, any image you create will be valid for, say, DVI 5.0.0 and OpenLiteSpeed. You will not be able to create any NGINX servers until you remove the custom image from the provider settings OR you create a virtual provider without a custom image.

And, you will need to recreate the image for the next version of DVI (major or minor).

If your custom image does not have anything to do with the DVI 5.0 install (eg: you’re adding some other packages you need later or you just want to make sure your starting image has all the latest Os updates), then you will not have an issue.

But if you use a custom image based on an initial standard DVI server installation, then these restrictions apply.

## Other

Each OS requires a different custom image.

Care must be taken that you provide the correct ID for each OS. Otherwise, you might end up deploying an Ubuntu 18.04 server when requesting an Ubuntu 22.04 server – we will not know the difference and will tag the server with 22.04. This will, as you might expect, cause all kinds of issues!

## Supported Providers

The following providers support custom images:

*   AWS EC2

We have the ability to quickly add support for the following providers if it is a gating factor in your deployment:

*   DigitalOcean
*   Vultr
*   Linode

Just open a support ticket and let us know if you need it. However, please do not ask us to add this feature to the above listed providers if you do not really need it!

## Troubleshooting

If you are seeing weird or unexplained behavior with your servers, please remove the custom image ids from your settings area and try deploying the server with the default OS images.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Microsoft Azure Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/microsoft-azure-provider-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240304154342/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
