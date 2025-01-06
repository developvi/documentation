---
title: "Notes for cloning sites, changing servers & changing domains"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Notes for cloning sites, changing servers & changing domains
  parent: 02-User-guide
  order: 14
---
When cloning a site or changing a domain name you MIGHT encounter a number of issues. Whether you encounter these issues or not is dependent on the site you’re copying, the sequence of steps you take and so on. Regardless, if you do run into these issues, here are instructions for resolving them.

## Cloning A Site To A New Server – Object Caching

If you push a site to a new server then you need to make sure that you either:

1.  Turn on the SAME object caching mechanism as the original server (Redis or Memcached) or
2.  Turn OFF the object caching mechanism:
1.  To turn OFF the object caching mechanism, you need to delete the symlink for the object-cache.php file in the wp-content folder if it exists. If an object-cache.php file exists there instead then you should delete it as well.

## Backups

When a site is cloned to a new server, the backups are NOT transferred with it!

## Permissions After Cloning or Domain Name Changes

After cloning a site or changing a domain, plugins might start to complain about permission errors. This just means that you have to reset the permissions on the WordPress folders because the NGINX user for your site has changed (to match the new domain name). _If you need instructions then please contact our support team._

## Redirect Issues After Cloning or Domain Name Changes

After cloning a site or changing a domain you might find that navigating to the new domain somehow takes you back to the original domain. Here are some possible causes:

1.  The DNS for the new domain is not pointing to the new server (if you moved servers)
2.  The object cache is not cleared. If you are running an object cache, the best thing to do is to flush the cache and then restart the object cache service.
3.  Double check your wp-config.php to make sure that there are no references to the old site in there. (See a possible related issue in Multisite in the next session)
4.  It is possible that the main sites table still have the old domain referenced. Using **phpMyAdmin**, check the _wp\_blogs_ and _wp\_options_ table. The old domain will likely be in one of the first few rows of those two tables. (Note that the _wp\__ table prefix might be different for your site. It could something random such as _hquXT\_._)
5.  Definitely try clearing cookies for both the new site and old site in your browser. It is possible that a cached redirect still exists there and that the browser is just not picking up the new domain without a redirect.

## Potential Multisite Issues

When pushing a multisite to a new server or cloning a multisite or changing a domain on a multisite, you’ll need to make some adjustments after files and data have been copied:

1.  Update _wp-config.php_ to make sure that _DOMAIN\_CURRENT\_SITE_ is set to match your new domain (if you changed domains).
2.  If you do not see the _DOMAIN\_CURRENT\_SITE_ entry in wp-config it means that the site is no longer considered a multisite. To easily resolve this, go to the **MULTISITE** tab in the DevelopVIDeploy control panel and toggle the Multisite option to ON – it will update the _wp-config.php_ file. Then, double-check the _DOMAIN\_CURRENT\_SITE_ entry in _wp-config.php_.
3.  If you have changed the domain on a MultiSite then the subsite domains in the **MULTISITE** tab in the DevelopVIDeploy control panel need to be updated. You should delete the existing subsites that are there and re-add them. (Deleting them from there does not delete them from your database, it just deletes them from our stored metavalues so you can re-add the new references).

We’re hoping to check for and automate away some of these issues in a future version of DVI but, for now, you should be aware of them and contact our support team with any questions or issues you might have.

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240304143309/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
