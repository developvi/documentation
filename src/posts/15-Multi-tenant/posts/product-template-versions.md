---
title: "Product Template Versions"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Product Template Versions
  parent: 15-Multi-tenant
  order: 5
---
You can create a version of your Product Template site at any time. At the very top of the Multi-tenant tab for the template you’ll see the **CREATE A NEW VERSION** section.

[![](https://web.archive.org/web/20240304134434im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-02.png)](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-02.png)

Creating a new version results in two things happening:

*   A new site is cloned from the product template site
*   Files are tagged in your git repository and GitHub with your new version id.

Since GIT is being used here, you need to make sure that you have committed all your changes using the **COMMIT & PUSH** button on the GIT tab BEFORE creating a new version.

Some things to keep in mind:

*   Your version ID should not have any spaces in it and should be restricted to letters, numbers, dashes, underscores and periods.
*   Version IDs need to be unique across all your templates. So if you have three templates, you should probably start (or end) each version ID with a different number or letter to make sure you don’t accidentally use the same version ID in different templates. Right now we do not validate the uniqueness of this ID since the intention is to remove this restriction in a future version.
*   If Cloudflare integration is enabled, you will see a suggested domain automatically populate the domain field. You can, of course, change this as you see fit.
*   You should make sure there is enough space on your server – a safe rule of thumb is to make sure there is 3x the space used for the template site available.

You can create a version at any time. As versions are created, they will be listed in the **EXISTING VERSIONS** section of the MULTI-TENANT tab.

[![](https://web.archive.org/web/20240304134434im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-03.png)](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-03.png)

## Setting a Default Version

For some operations (eg: Selling Site Subscriptions with WooCommerce), you will need to specify a default version. This is also called the PRODUCTION version.

[![](https://web.archive.org/web/20240304134434im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-04.png)](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-multi-tenant-04.png)

The default version is the one that will be used in certain site creation operations if no other version is specified.

## Versions & Tenants

Creating a new version or setting a production/default version does not automatically upgrade existing tenants. All tenants remain on their existing version until you designate them for an upgrade.

If you do not upgrade your tenants, they will remain on the version that you designated at the time the tenant site was deployed.

## Notes

After a version is created, it is a stand-alone site. You should back it up at least once using the DVI backup option (or a backup plugin that is part of the template) and ensure that the backup is stored off-site. Or, if the template server is being backed up by your provider, that will suffice as well.

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Create A Tenant](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304134434/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
