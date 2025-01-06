---
title: "Enabling Multisite"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Enabling Multisite
  parent: 23-Multisite
  order: 3
---

To enable multisite:

1.  _We strongly recommend that you BACKUP your site before proceeding with the rest of these instructions_
2.  Go to DevelopVIDeploy → Applications
3.  Locate your site and click on the title to navigate to the detail page.
4.  Under the _MULTISITE_ tab you will see three buttons – one for each type of Multisite. Click the button for the type of Multisite you need.

[![](https://web.archive.org/web/20240420014506im_/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-080.png)](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-080.png)

That should be it. When you log into the site again, you should see the network menu option in the WordPress topbar.

## Notes

*   If you are creating a new Multisite and not restoring an existing multisite from backup, we suggest that you enable Multisite before you add too many plugins or themes to your site. Many plugins and themes do not support Multisite cleanly so enabling Multisite with these installed might result in unexpected behavior. Or, worse, your site crashes because a plugin or theme that isn’t Multisite compatible throws a hard error.
*   If your site already has SSL enabled, you will need to disable it before converting it to a multisite. You will not be shown any Multisite options until SSL is disabled. Once Multisite is enabled, you will have a new, expanded set of SSL options in the MULTISITE tab.
*   It is recommended that your PHP memory allocation be at least 256M and that wp-config memory limit options be configured to also allow for at least 256M.

### More Topics In Multisite

*   [Multisite: Installing the Add-On](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-installing-the-add-on/)
*   [Multisite: Introduction](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-introduction/)
*   [Enabling SSL For the Multisite Network](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-ssl-for-the-multisite-network/)
*   [Add A Site To The Multisite Network](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/add-a-site-to-the-multisite-network/)
*   [Enable or Disable SSL For A Subsite On A Multisite Network](https://web.archive.org/web/20240420014506/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enable-or-disable-ssl-for-a-subsite-on-a-multisite-network/)
