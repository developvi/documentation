---
title: "Multisite Introduction"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Multisite Introduction
  parent: 23-Multisite
  order: 2
---
Multsite on WPCloud Deploy is a bit different from other hosting platforms. Depending on the type of Multisite you need and the type of SSL certificate you’ll be employing, the workflow can be quite different.

So, we suggest that you read through this entire Multisite documentation section before activating multisite on your WordPress instance.

### Terminology Notes

In this documentation we use the term SUBSITE or CHILD SITE to refer to a site on the Multisite network. This helps to avoid confusion over whether we’re talking about the main network site or a site on the network.

## Multisite Types & Options

There are three types of Multisites in DVI, two related to subdomains and one related to subdirectories.

### Option #1: Subdirectories

This is the simplest Multisite option but it is _only supported in DVI 4.6.0 and later_. With this option you only need to set up SSL once for the main site and all the other sub-sites will be protected. And, there are no other steps to configure new subsites – unlike the other two options below.

Oh, and subdirectories do not support mapped domains.

### Option #2: Subdomains – Individual SSL

With this option your subsites can be accessed using a URL such as _subdomain.mymaindomain.com_.

When you select this option you will need to do two things for each subsite:

1.  Set up each subsite under the DVI Multisite screen – _this setup process creates the NGINX (webserver) configuration files that redirects traffic to the subsite._
2.  Set up SSL for the subdomain using the SSL options under the DVI Multisite screen.

This option supports mapped domains.

### Option #3: Subdomains – Wildcard SSL

With this option you only need to configure the SSL certificate once. But because of security concerns with wildcard certificates, it requires specialized support for each domain provider. We only support CLOUDFLARE at this time. _If your domain cannot be transferred to CloudFlare’s nameservers then you will not be able to set up Wildcard SSL in DVI._

Once you have issued the SSL wildcard certificate, all further subdomains are automatically protected with it.

This option supports mapped domains.

_The Wildcard subdomain feature is only supported in DVI 4.6.0 and later._

### More Topics In Multisite

*   [Multisite: Installing the Add-On](https://web.archive.org/web/20240304142344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-installing-the-add-on/)
*   [Enabling Multisite](https://web.archive.org/web/20240304142344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-multisite/)
*   [Enabling SSL For the Multisite Network](https://web.archive.org/web/20240304142344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-ssl-for-the-multisite-network/)
*   [Add A Site To The Multisite Network](https://web.archive.org/web/20240304142344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/add-a-site-to-the-multisite-network/)
*   [Enable or Disable SSL For A Subsite On A Multisite Network](https://web.archive.org/web/20240304142344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enable-or-disable-ssl-for-a-subsite-on-a-multisite-network/)
