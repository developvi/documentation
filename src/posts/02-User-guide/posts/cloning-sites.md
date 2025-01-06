---
title: "Cloning (Copying) Sites"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Cloning (Copying) Sites
  parent: 02-User-guide
  order: 9
---
DevelopVIDeploy makes it easy to copy a site to a new domain on the same server. This process is called “Cloning”.

To clone a site:

*  Go to DevelopVIDeploy → Applications
*  Click on the site for which this action will apply
*  Click on the _Clone Site_ tab
*  There should only be a single section on this screen. Enter your domain name for the new site.
*  Click the _Clone Site_ button
*  Click the _OK_ button in the confirmation window

A popup will appear that will offer periodic feedback as the cloning process progresses.

When the process is complete you will get a popup confirmation message and the black ‘terminal” window will show the actions that were taken while cloning the site. In particular the “terminal” window will provide an idea of all the search and replaces that were done in order to update the site with the new domain name. You can also see this information in the _COMMAND LOG_ screen.

## Before Cloning A Site

Please make sure that there is enough disk space on the server to clone the site. You can use the options under the _Statistics_ tab to see how much disk space is being used by the site. If the cloning fails because of a lack of disk-space, your new site will be left in an undefined state and you will need to use our PAID support resources to help you clean up the site on your server.

## Cloning Large Sites

When cloning large sites, you might see some “file not found” errors in the terminal. This is because it is taking a very long time to copy the files and, while that is happening, there is no output being sent to the log files.

If you know that your site is large then you should be patient and let the clone run a bit pass all those error messages.

Other error messages you receive might be from plugins – these are generated after the clone is complete and we are attempting to run some post-clone commands. Many plugins just don’t like being loaded on the command line and so throw up a bunch of errors. For the purposes of the clone operation, you can ignore these. **_In rare cases, really badly behaved plugins and themes will error out and cause the post-clone commands to fail._** If this happens, you might need to take a backup instead and do a manual restore in order to get a clone of the site.

## After Cloning A Site

*  We strongly suggest that you clear the OBJECT CACHE (such as MemCached or REDIS) if it’s enabled.

## Multisite Considerations

When cloning a MULTISITE installation of WordPress you might have to do some clean up work in order to get the new network to function properly:

1.  Change the DOMAIN\_CURRENT\_SITE entry in wp-config.php to point to the new domain.
2.  Add all the subsites into the MULTISITE tab in the DVI Dashboard for the new domain.
3.  Re-request SSL certificates for all the subsites in the new domain.

You might also need to request an SSL certificate for the main site as well.

## Notes

*  It is possible that the WP-CLI commands that run to change the domain (after the site has been copied) may fail. This usually occurs because one or more plugins or themes throw an error when WP-CLI is running – you’ll see the errors in the logs. The easiest way to work around this is to disable the plugins you have before cloning and then re-enable them after the cloning process has been completed.
*  When cloning an OLS site, the PHP version will always be the DVI default (currently 8.1). When cloning an NGINX site, the PHP version will be the same as the original site.
*  A cloned site starts with a new default VHOST configuration file. This means that items such as 7G/6G, tweaks, web-server redirects and HTTP AUTH are NOT copied to the new site.
*  Cloned sites do not inherit backup configurations
*  Cloned sites do not inherit the LINUX CRON setting – the sites default back to the core WordPress CRON process.

- - -

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240420015855/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
