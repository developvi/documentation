---
title: "Tips, Troubleshooting & Limitations"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Tips, Troubleshooting & Limitations
  parent: 15-Multi-tenant
  order: 11
---
## Plugins & Theme Dependencies

Some plugins and themes have dependencies. ALL dependencies must be installed in the product template site – your theme/plugin will not be able to download them for each individual site because the shared plugins & themes folder will be read-only.

For example, a Kadence theme might need to install plugins to support some of their functionality. This needs to be installed on the Product Template site.

## Incompatible Plugins

Some plugins and themes make assumptions as to the absolute location of dependent files. They will not work in a multi-tenant environment since the _plugins_ and _themes_ folders are no longer under the _wp-content_ folder.

While plugins that make assumptions are few and far between, a notable example is the BREAKDANCE page builder – tenant sites will not work when this plugin is used.

## Cloning Sites – Local Clones

When cloning sites to the same server (standard clones), the Multi-tenant attributes are cloned but with some modifications:

*   Tenant sites are cloned as a new tenant.
*   Version sites are tagged as ‘_mt\_version\_clone_‘ instead of ‘_mt\_version_‘
*   Template sites are tagged as ‘_mt\_template\_clone_‘

In some cases you might need to change the site type after the clone operation. For example, you might be cloning the Template site to use as the start of a new template. In this case you will want to remove the ‘_mt\_template\_clone_‘ designation. You can do this in **TOOLS** section of the MULTI-TENANT tab.

## Cloning Sites To New Servers (Site-Sync / Copy To Server)

When pushing sites to another server, the Multi-tenant attributes are cloned but with some modifications:

*   Tenant sites are cloned as new tenant sites – but unless the target also contains the appropriate _wpcd-mt-versions_ folder, the site will not work.
*   Version sites are tagged as ‘_mt\_version\_clone_‘ instead of ‘_mt\_version_‘
*   Template sites are tagged as ‘_mt\_template\_clone_‘

In some cases you might need to change the site type after the clone operation. For example, you might be cloning the Template site to use as the foundation for a new template. In this case you will want to remove the ‘_mt\_template\_clone_‘ designation. You can do this in **TOOLS** section of the MULTI-TENANT tab.

## Site-Specific Plugins & Themes

We mentioned in our [Introduction to Multi-tenant](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/) that we symlink individual plugin and theme folders instead of the wp-content/plugins and wp-content/themes folders.

We do this because it allows an admin the flexibility to add plugins that are specific to a customer – by uploading them to the wp-content/plugins or wp-content/themes folder for a site.

However, for this to work, the plugin/theme has to be uploaded via sFTP – you cannot use the PLUGINS/THEMES screen to upload them. The wp-content/plugins and wp-content/themes folders are protected by default against uploads from wp-admin.

After uploading, you might also need to login via sFTP and change the permissions of the newly uploaded plugin/theme folder.

Finally, updates to those plugins/themes will need to be handled via sFTP as well (unless you change their permissions).

## Remote Database Servers

One limitation of the default behavior of DVI Multi-tenant is that the database servers have to be on the same server as the web server.

To use remote databases you will need to utilize our professional services folks to make the change. This is one reason why the Multi-tenant module is only available as part of a professional services contract.

Among other things, remote database servers need proper user permissions configured to allow our scripts to create new databases on the server (each tenant has it’s own database). And, of course, we’ll need to configure our own multi-tenant scripts and such to use the remote server instead of the local servers.

## Old Template Versions

After a while you will not be using older versions of templates. We recommend that you DISABLE these old versions using the **ENABLE/DISABLE** option under the **MISC** tab.

## Multisite

Tenant sites cannot be converted to Multisite.

## How To View The Real File Location For A Symlink

If you want to see where a link points to, you can run the following command:

su <linuxuser> -c 'readlink -v "<symlink-file>"'

For example, if you want to see where the akismet.php file really points to for domain _mydomain.com_, you can use:

su <linuxuser> -c 'readlink -v "/var/www/mydomain.com/html/wp-content/plugins/akismet/akismet.php"'

Of course, replace <linuxuser> with a valid Linux user!

- - -

### More Topics In Multi-tenant

*   [Introduction to Multi-tenant](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/introduction-to-multi-tenant/)
*   [Multi-tenant Components & Concepts](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/multi-tenant-components-concepts/)
*   [Getting Started With DVI Multi-tenant](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/getting-started-with-wpcd-multi-tenant/)
*   [Template Sites (Product Templates)](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/template-sites-product-templates/)
*   [Product Template Versions](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/product-template-versions/)
*   [Create A Tenant](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/create-a-tenant/)
*   [WooCommerce Integration](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/woocommerce-integration/)
*   [Upgrading Tenants](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/upgrading-tenants/)
*   [Using Multiple Servers (Horizontal Scaling)](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/using-multiple-servers-horizontal-scaling/)
*   [Hooks, Filters Etc.](https://web.archive.org/web/20240304153916/https://wpclouddeploy.com/documentation/multitenant/hooks-filters-etc/)
