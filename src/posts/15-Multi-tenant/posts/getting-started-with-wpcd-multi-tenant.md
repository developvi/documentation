---
title: "Getting Started With DVI Multi-tenant"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Getting Started With DVI Multi-tenant
  parent: 15-Multi-tenant
  order: 3
---
## Pre-requisites

Before you can use the DVI Multi-tenant module you need the following:

*   Install and activate the [DVI GIT module](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/).
*   If you intend to allow your customers to purchase their own sites you’ll need to install and [DVI WooCommerce module](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/) as well as the WooCommerce and WooCommerce Subscriptions plugins.

## Activating Multi-tenant Options

Multi-tenant is a premium option offered only as a combined software + services product. The software (plugin) is not available without the services component.

The software itself is provided as a regular WordPress plugin created by our services group – upload and activate it from the WordPress PLUGINS screen.

Once activated you will see the following:

*   A new Multi-tenant tab under each site

## Restrictions

Currently, Multi-tenant features are only supported on NGINX webservers and on server providers who allow ‘root’ logins. This means that providers such as AWS, AZURE and GOOGLE are not supported. We hope to remove these restrictions shortly.

- - -

## Next Steps

*   Deploy a server that will store your template sites, version sites and tenant sites. This is the simplest multi-tenant configuration where everything resides on a single server. You’ll want lots of disk space to start since you will likely be experimenting with multiple templates and versions of those templates
*   [Create a product template site](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Create one or more versions of your template](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   Specify a default version (see **SETTING A DEFAULT VERSION** in the [product template versions](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/) documentation)
*   Create a WooCommerce product (see [WooCommerce Multi-tenant Integration](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/) & the standard [WooCommerce Integration](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/) documentation)
*   Go through the customer purchase process in a separate browser

- - -

## Support Policy

_As mentioned in our [introduction to Multi-tenant document](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/), this module is only available with a [services or upgraded support contact](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/downloads/multi-tenant-module-services-enhanced-support/). Software developers can grab the code our [github repository](https://web.archive.org/web/20240304135652/https://github.com/wpclouddeploy/wp-cloud-deploy)._

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304135652/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
