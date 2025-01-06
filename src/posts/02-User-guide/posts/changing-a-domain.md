---
title: "Changing A Domain"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Changing A Domain
  parent: 02-User-guide
  order: 13
---
When changing domains on your WordPress site you have three options:

1.  **Quick Change:** With this option, only the two core records in the WordPress database are changed. Any links or references to the old domain that are contained in posts and pages remain behind. This process is QUICK as the name implies.
2.  **Full – Dry Run:** This option allows you to run a search and replace in your database to find as many places as possible to change the old domain to the new domain. But it only reports what it finds – it doesn’t actually perform the changes.
3.  **Full – Live:** This option allows you to run a search and replace in your database to find as many places as possible to change the old domain to the new domain. This option performs the changes and is NOT reversible.

Most users will likely want to use option 3.

Additionally, option 1 and 3 will attempt to issue a new SSL certificate for the new domain. This will fail if the DNS has not been updated to point the new domain to the server before the process starts.

To change a domain for a regular WordPress site:

*  Make a backup of site. Better yet, make multiple backups since the process is irreversible!
*  If the current domain has an SSL certificate then make sure that your DNS is updated to point the new domain to the server (so that an SSL certificate for the new domain can be issued.)
*  **If one is enabled, disable the object cache (MemCached or Redis) for the site.** This is suggested because direct changes to the database tend to cause the caches to become outdated and some plugins do not take that into consideration. Thus, its safer to always disable the object caches before doing direct database operations such as changing domains.
*  Go to WPCloud Deploy → Applications
*  Click on the site for which this action will apply
*  Click on the _Change Domain_ tab
*  Enter your new domain
*  Click on one of the three buttons to do a quick change or perform a full dry or live run.
*  Click the _OK_ button in the confirmation window

A popup will appear that will offer periodic feedback as the process progresses.

When the process is complete you will get a popup confirmation message and the black ‘terminal” window will show the actions that were taken while changing the domain for the site. You can also see this information in the _COMMAND LOG_ screen.

## After Changing The Domain

*  We strongly suggest that you clear the OBJECT CACHE (such as MemCached or REDIS) if it’s enabled.
*  For multisite installations you might see an _“**Error**: Cookies are blocked or not supported by your browser. You must enable cookies to use WordPress.”_ message when you try to log into wp-admin. In this case try adding the following to your wp-config.php file: _define( ‘COOKIE\_DOMAIN’, false );_

## Notes

This option is highly dependent on your PHP script timeout and so might not work for your large sites. For large sites you can run the BASH script from the command line – please contact our support group so we can walk you through the process of using that script.

It is possible that the WP-CLI command that runs to change the domain may fail – this usually occurs because one or more plugins or themes throw an error when WP-CLI is running. You’ll see the errors in the logs. The easiest way to work around this is to disable the plugins you have before changing your domain and then re-enable them after the domain has changed.

## Multisite Considerations

When changing the domain for a MULTISITE installation of WordPress you will have to do some clean up work in order to get the new network to function properly:

1.  Change the DOMAIN\_CURRENT\_SITE entry in wp-config.php to point to the new domain. This should be done already but it’s good to double-check.
2.  Add all the subsites into the MULTISITE tab in the DVI Dashboard for the new domain.
3.  Re-request SSL certificates for all the subsites in the new domain.

You might also need to request an SSL certificate for the main site as well.

## sFTP Side-Effects

When a domain has changed, sFTP users need to be REMOVED and re-added. This is because the sFTP user was provisioned for the old domains’ folder names which have all been changed to the new domains’ name.

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240529155621/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
