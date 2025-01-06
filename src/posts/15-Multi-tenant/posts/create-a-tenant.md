---
title: "Create A Tenant"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Create A Tenant
  parent: 15-Multi-tenant
  order: 6
---
New tenants are created from a versioned site. They are not created from the template.

Templates → Version → Tenant

or

Local Dev → Templates → Version → Tenant

You use your template as your development site. When you’re satisfied with it you [create a version](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/). Tenants are created from a particular version.

There are three methods you can use to create a tenant:

### Option 1: Purchase via WooCommerce

The most common use-case for multi-tenancy in WordPress is as part of a SaaS project. Thus, it is the most straight-forward way to create a tenant.

1.  Create a WooCommerce product where the template is a Multi-tenant template site. You only need to do this once for each template you’re using (but you can, of course, create as many products as you like from the same template.)
2.  Just go through the normal checkout process for that newly created product.

- - -

### Option 2: Clone a Version

Cloning a site means that the initial clone lives on the same server as the versioned site (which generally is the same as the Template server as well.)

*   Navigate to the versioned site in your site list and open it.
*   Click on the CLONE SITE tab
*   Clone the site

**(Optional) Copy Clone To New Server**

Next you need to decide if you want the cloned site to continue to live on the same server as the versioned site or push it to a different server.

If you push it to a different server, you also need to make sure that the target server has already received copies of the versioned sites (see the **PUSH VERSIONS TO REMOTE SERVER** section on the MULTI-TENANT tab of the template site).

To push the clone to a different server, use the options under the **COPY TO SERVER** tab for the new clone. Then you can delete the original clone from the template server. Don’t forget to change your DNS to point to your new server IP.

Finally, once the clone is where you need it to be, navigate to the MULTI-TENANT tab (of the cloned site) and use the **CONVERT** button to make it a tenant.

- - -

### Option 3: Convert an Existing Site

You can take an existing site and convert it to a tenant. It is rare that you would need to do this.

**With this process you lose all data in the database for the existing site**.

The only thing that remains is the use of the domain and, in some cases, the files in the UPLOADS folder and some non-standard folders in _wp-content_.

There are two steps to this process:

1.  Copy the versioned site to the existing site and
2.  Convert the site to a tenant

The full sequence of steps are as follows:

*   Navigate to the version you wish to use for the existing site.
*   Click on the **COPY TO EXISTING SITE** tab
*   Enter the domain of the existing site
*   Click on the **PUSH EVERYTHING** button.
*   When that is complete, navigate to the existing site and click on the MULTI-TENANT tab.
*   Select the product template and the version you wish to associate with this site
*   Click the **CONVERT** button.

With this process you might be missing some content from the wp-config.php file. This is because we do not copy the wp-config.php file when we use the COPY TO EXISTING SITE function.

- - -

## Notes About Tenant Sites

*   Cloning a tenant site will clone symlinks so it will also exist as a tenant.
*   When you copy a tenant site to a new server, all files will be copied including plugins, themes etc. However, you will need to use the RESET PERMISSIONS button in the TOOLS tab for the new site before you can perform certain operations such as updating plugins and themes.
*   When we backup a tenant site, we will not be backing up the full suite of plugins, themes etc. – we will only be backing up the symlinks.

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304155550/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
