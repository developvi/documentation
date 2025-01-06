---
title: "WooCommerce Integration"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WooCommerce Integration
  parent: 15-Multi-tenant
  order: 7
---
DVI Multi-tenancy features are tightly integrated with our WooCommerce module.

In particular, you can specify a Multi-tenant template site for a WooCommerce product and DVI will figure out how to get the latest or default version of that template and use it for the new customer site.

[![](https://web.archive.org/web/20240304160608im_/https://wpclouddeploy.com/wp-content/uploads/2023/01/wpcd-multi-tenant-08.png)](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/wp-content/uploads/2023/01/wpcd-multi-tenant-08.png)

In a single server architecture where Templates, Versions and Tenants reside on the same server, you don’t have to worry a lot about how this all works – just set things up the way you normally would (see our [Sell Sites With WooCommerce](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/) documentation.)

In an environment where you have multiple tenant servers, you do need to pay attention to the processes we outlined in the [Using Multiple Servers](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/) document.

**Note: You MUST make sure that your Template site has a default (production) version specified!** Please see the **SETTING A DEFAULT VERSION** section of the [Multi-tenant Product Template Site](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/) document.

## Using A Specific Version

If you specify a template site for a WooCommerce product, we will use the default (production) version of the template for all new tenant sites.

However, you can specify any version site as well and DVI will use just that version for new tenant sites.

But, as we mentioned earlier, in an environment where multiple tenant (customer) servers are deployed, you need to follow the rules outlined in the [Using Multiple Multi-tenant Servers](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/) section of our documentation.

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304160608/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
