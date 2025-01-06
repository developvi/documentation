---
title: "PHP 8.0-8.1-8.2 & 8.3 Notes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: PHP 8.0-8.1-8.2 & 8.3 Notes
  parent: 01-cloud-deploy-core
  order: 15
---
# PHP 8.0, 8.1 & 8.2 Notes

## PHP 8.0 & 8.1

DevelopVIDeploy Version 5.0 and later **will work on PHP 8.0 and 8.1**.

However, not all server providers will work cleanly on those PHP versions. This is because their PHP API wrappers have not yet been updated to support those versions. Once updated, we’ll update our code to use them. Until then there will be some limitations as described below.

The following providers should work cleanly with PHP 8.0 & 8.1

*   DigitalOcean
*   Linode
*   Vultr

The following providers **will work** but might throw deprecation and other warnings in the debug.log file (but only if you have your WordPress debug log flags turned on):

*   Alibaba
*   AWS EC2
*   AWS Lightsail
*   Azure
*   Exoscale
*   Google
*   Hetzner
*   OpenStack
*   Proxmox
*   UpCloud

## PHP 8.2

In DevelopVIDeploy version 5.3 and later you can activate PHP 8.2 for your client sites. This should be considered beta support since many components in the WP ecosystem are nowhere near ready for PHP 8.2.

DVI itself will not be certified to run under PHP 8.2 until WordPress officially supports it along with the PHP API libraries for the various Cloud Server Providers. For now, consider running DVI with PHP 8.2 as beta.

## WordPress Support For PHP 8.x

This table on the MAKE WORDPRESS site shows the official WP support for PHP 8.x: [https://make.wordpress.org/core/handbook/references/php-compatibility-and-wordpress-versions/](https://web.archive.org/web/20231001075802/https://make.wordpress.org/core/handbook/references/php-compatibility-and-wordpress-versions/)

As of the date this article was last updated, PHP 8.0, 8.1 & 8.2 were all stilled tagged as “beta”.

- - -

Last updated June 21st, 2023



