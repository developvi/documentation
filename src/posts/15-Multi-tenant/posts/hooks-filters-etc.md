---
title: "Hooks, Filters Etc."
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Hooks, Filters Etc.
  parent: 15-Multi-tenant
  order: 12
---
You can create your own function that bypasses our script that creates and updates tenant files. With these lifecycle hooks you can do some every powerful things such as:

*   Symlink the full plugins or themes folder instead of individual folders
*   Symlink core files and dynamically edit them to use a single version of the WP Core
*   Run custom upgrade routines using wp-cli and your custom plugins
*   Handle thorny plugin and theme licensing issues
*   etc.

Learn more about some of the scripts in the read-me file in the _wp-content/plugins/wp-cloud-deploy/includes/core/apps/wordpress-app/scripts/v1/multi-tenant-pre-post-samples_ folder.

You also have access to the usual external custom scripts as described in the [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/) document.

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304142733/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
