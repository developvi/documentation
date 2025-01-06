---
title: "Multi-tenant Components & Concepts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Multi-tenant Components & Concepts
  parent: 15-Multi-tenant
  order: 2
---
Multi-tenancy introduces a number of new concepts into DevelopVIDeploy:

*   Template Sites
*   Versions
*   Product Templates
*   Site Types

### Template Sites

Template sites are the sites on which all your tenant sites are based. It is the development version of your tenant sites.

### Version

When you add a tenant, you are adding them to a particular version of a template site.

You can think of your template site as you development site. And the versions are the point-in-time snapshots that will be used to create your tenant sites.

Versions build upon Git Tags. Where-as a Git Tag gives you a point in time for a set of files, a DVI template version includes a Git Tag for the files as well as a full clone of the template at the time the version was created.

*   The full site is used for new tenants – this includes both the files and database.
*   The Git Tagged files are used to upgrade existing tenants to new versions. Only files are upgraded on existing sites. To update the database you usually create a custom plugin that contains the database update logic.

When a new version is created from the Multi-tenant tab, a Git Tag is created as well as a full clone of the template site.

### Product Template

A Product Template (aka DVI Product) is another name for a template site. It’s, in effect, a synonym for the domain of the template site.

For example, the domain for your template site might be _legalbusiness.mydomain.com._ But you can set a name for the template to something more friendly such as “_My Legal Business Template_“.

You might find us using the term “template site”, “product template” and “DVI Product” interchangeably.

One thing to keep in mind is that a PRODUCT TEMPLATE is NOT a WooCommerce product. They are very very different things.

A WooCommerce product can be based on a Product Template (template site) and multiple WooCommerce products can be defined against one Product Template (template site).

## Site Types

Without Multi-tenancy, DevelopVIDeploy deals with only two types of sites:

*   Standard Sites
*   Template Sites (If WooCommerce integration is activated)

The DevelopVIDeploy Multi-tenant premium module adds quite a number of additional site types:

*   **Version Sites** – these are clones of template sites that represent a version. They are used when creating sites for new tenants.
*   **Version Clone** – these are **Version Sites** that are copied to other servers.
*   **Tenant Site** – These are, well, tenant sites. There can be a mixture of standard sites and tenant sites on the same server or across multiple servers.
*   **Template Clones** – These are templates that are copied to other servers. For now, there is no practical use for this but we’re keeping an open mind for future use.

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240529143233/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
