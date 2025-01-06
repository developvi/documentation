---
title: "Introduction to Multi-tenant"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Introduction to Multi-tenant
  parent: 15-Multi-tenant
  order: 1
---
## Introduction

A multi-tenant installation is similar to a WordPress Multisite install. But, it has a number of advantages over a WordPress Multisite:

*   It is more scalable
*   It is compatible with more plugins and themes
*   It is easier to export out to a stand-alone site if necessary
*   It is easier to backup and restore single sites
*   In some cases you can even import an existing site and make it a part of a multi-tenant structure

However, there are disadvantages:

*   It is more complex to setup compared to WP Multisite and WPUltimo
*   There is no ‘standard’ install – each multi-tenant provider has a different method of creating the multi-tenant infrastructure and deploying sites
*   It requires minor mods to core WP files
*   Some plugins and themes might not be compatible because they make assumptions on the relative locations of files
*   A mistake or infection can easily bring down all your clients
*   It’s harder to apply across multiple servers

## DevelopVIDeploy Multi-tenant Features

Our implementation of Multi-tenant WordPress provides the following advanced features (in addition to the typical multi-tenant features)

*   Versioning
*   Distributed multi-server deployments
*   Rolling upgrades
*   Git integration
*   WooCommerce Integration
*   Lifecycle hooks
*   Managed via a UI instead of the command line

## Typical Install

A typical multi-tenant structure will have a single version of WordPress and the plugins and themes folders. It will have its own database and downloads folder as well as any other unique folders required by a plugin or theme.

However, we **have decided to implement Multi-tenant slightly differently**. We make two changes to the ‘shared files’ model which allows us to offer the advanced features mentioned above:

#### 1\. No Sharing Of WP Core Files

DVI Multi-tenant will share a single install of Plugins and Themes among all tenants. **But each tenant site will have its own copy of WordPress core files** \[instead of sharing a single copy among all tenants.\]

The reason is simple – to share WP core we would have to modify the core files. Granted, they would be minor modifications in index.php and at the bottom of wp-config.php (the area below the warning “stop editing now”) among others. But we don’t want to burden developers with having to handle those mods or track them as WP rolls out upgrades.

And we gain a couple of advantages including:

*   Any 3rd party developers you might employ to manage things for you don’t have to worry too much about the non-standard structure for core files – they can continue to use what they know

Of course, we provide the management tools inside DVI so that this doesn’t become a burden. You’ll still be using our point-and-click UI to perform the standard Multi-tenant tasks such as

*   Create versions
*   Deploy versions
*   etc.

Behind the scenes we’ll be handling all the core files as needed to make everything work.

Still, if you really Really REALLY want to have a single WP installation, we’ve provided all the lifecycle hooks necessary to restructure and dynamically edit files when creating a tenant.

#### 2\. Sym-linking Individual Plugins & Theme Folders

In a typical Multi-tenant structure, the root plugins and themes folders, “_wp-content/plugins_” and “_wp-content/themes_“, are symlinked to each site. (A symlink is just a special file that points elsewhere on the file system – similar to Windows shortcuts.)

DVI, however, symlinks the folders one level lower – the individual plugin and theme folders. The reason is that this allows the admin to add plugins and themes that are unique to a site without impacting other sites. You can mix symlinks and standard files inside the plugins and themes folder for each site.

You might not need this flexibility, in which case you can use our life-cycle hooks to change which folder is symlinked. (In the future we might offer you the option when you create a template as to which level you want the themes & plugins folders to be linked.)

## Additional Reading

You can learn more about the different approaches to WordPress Multi-tenant using the following resources.

*   [Multi-tenant WordPress](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/audience/multi-tenant-wordpress/)
*   [The Ultimate Guide to Building a WordPress SaaS](https://web.archive.org/web/20240304135111/https://opensaas.io/the-ultimate-guide-to-building-a-wordpress-saas)
*   [Github – Multi-tenant quick-start for developers](https://web.archive.org/web/20240304135111/https://github.com/troychaplin/wp-multitenant)
*   [OpenSaaS Articles](https://web.archive.org/web/20240304135111/https://opensaas.io/articles)

## WordPress Multitenant Resources

*   [WordPress SaaS: Multi-tenant vs Multisite vs Standard Sites](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/wordpress-saas-multi-tenant-vs-multisite-vs-standard-sites/)
*   [How To Restrict Plugin Access In A WordPress Multi-tenant SaaS](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/restricting-plugin-access-in-a-wordpress-multi-tenant-saas/)
*   [WordPress Multitenant SaaS: How To Add A WooCommerce Product ID To WP-CONFIG](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/wordpress-multitenant-saas-how-to-add-a-woocommerce-product-id-to-wp-config/)

- - -

_Important Note: The Multi-tenant module is only available as part of a services or upgraded support package. The module has a lot of moving parts so we fully expect that there will be many questions related to how best to apply it to your use-case and goals. Since that kind of in-depth, organization-specific support is not something we can reasonably provide for free in our ALL ACCESS bundle support, the only way to offer this feature is by making it part of a services or upgraded support contract._

_However, the code is opensource on GITHUB and experienced ALL ACCESS developers can use it as they see fit. Just keep in mind that this is not an install-and-go feature – it does require at least a smidgen of developer level work (hence the necessity for the services and support package)._

- - -

### More Topics In Multi-tenant

*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Tips, Troubleshooting & Limitations](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304135111/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
