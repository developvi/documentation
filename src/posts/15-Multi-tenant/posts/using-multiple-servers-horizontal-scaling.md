---
title: "Using Multiple Servers (Horizontal Scaling)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Using Multiple Servers (Horizontal Scaling)
  parent: 15-Multi-tenant
  order: 10
---
DVI Multi-tenant supports a distributed multi-server environment including:

*   Multiple Template Servers
*   Multiple Tenant (Customer) Servers

However, this environment requires a bit more configuration setup than one where template & customer (tenant) sites live on the same server.

## Multiple Template Servers

If you have multiple templates, you can divide them up among multiple servers. This is useful if you create a lot of versions and you have multiple templates. You can then split those templates across different servers.

There is no special configuration required for this – just initialize your template site as usual on any server.

If you need to to move a template from an existing template server to a new one it is a multi-step process:

*   Clone the template to the new server using the options on the COPY TO SERVER tab for the template
*   Clone the version site(s) to the new server using the options on the COPY TO SERVER tab for the template (you will repeat this step for each version site)
*   Use the **PUSH VERSIONS TO REMOTE SERVER** function on the MULTI-TENANT tab for the template to get the existing versions and related metadata to the new server
*   On the new template site record use the **CLEAR SITE TYPE** button in the TOOLS section of the MULTI-TENANT tab
*   On the new template site record click the **BREAK LINK** button in the TOOLS section of the MULTI-TENANT tab
*   On the new template site record click the **TEMPLATE FLAG** toggle in the MULTI-TENANT tab

## Multiple Tenant (Customer) Servers

In the most basic DVI Multi-tenant configuration, template sites (with their associated versions) and tenant sites live on the same server. But, you can create new tenant servers so that you do not have all your eggs in one basket.

On each new tenant server you will need to seed it with the version sites and related version files. To do this:

For Each Template:

*   Clone the version site(s) to the new server using the options on the COPY TO SERVER tab for the template
*   Use the **PUSH VERSIONS TO REMOTE SERVER** function on the MULTI-TENANT tab for the template to get the existing version files and data to the new server

So, if a template has 5 versions (this means 5 version sites), you will use the COPY TO SERVER function on each version to get them to the new tenant server. In many cases you can choose to copy only the latest PRODUCTION version since that’s the one most likely to be used for new tenants.

It is not necessary to copy the template itself to the new tenant server. Only the version sites need to be copied along with the version files (the 2nd bullet point above).

## Creating New Versions Addendum

**With multiple tenant servers, creating new versions require an extra step.**

Every time you create a new version that will be used for tenant (customer) sites, you need to repeat the steps above to ensure that each customer (tenant) server has all the files needed to create new tenants and upgrade existing ones.

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304144218/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
