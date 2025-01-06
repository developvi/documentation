---
title: "Enable or Disable SSL For A Subsite On A Multisite Network"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Enable or Disable SSL For A Subsite On A Multisite Network
  parent: 23-Multisite
  order: 6
---
The process for enabling SSL for a multisite varies depending on the type of Multisite that is in use.

## Standard (Non-wildcard) SSL Subdomains

To enable SSL for a subsite on a non-wildcard ssl subdomain multisite network, use the following steps:

1.  Go to WPCloud Deploy->Applications
2.  Locate your site and click on the title to navigate to the detail page.
3.  Click on the _Multisite_ tab.
4.  Scroll down to the _TOGGLE SSL FOR A SUBSITE_ section
5.  Select the subsite you want to work with from the site drop-down list
6.  Enter an email address – emails will be sent to this address when it’s time to renew the certificate for the site
7.  Click the **TOGGLE SSL** button.

If the DNS for your domain is properly configured to point to your server’s IP address then a certificate will be issued and SSL will be enabled for the site.

If you get an error, check the _WPCLoud Deploy->SSH LOG_ screen for a complete transcript of the action.

## Wildcard SSL Subdomains

For this option you need to enable SSL for the entire network. You might have already done this when you enabled SSL under the SSL tab.

1.  Go to WPCloud Deploy->Applications
2.  Locate your site and click on the title to navigate to the detail page
3.  Click on the _SSL_ tab
4.  Click on the SSL Status Toggle.

If the DNS for your domain is properly configured to point to your server’s IP address then a certificate will be issued and SSL will be enabled for the site.

If you get an error, check the _WPCloud Deploy->SSH LOG_ screen for a complete transcript of the action.

## Subdirectories

Follow the same process above for _Wildcard SSL Subdomains_.

## Mapped Domains For Both Wildcard and Non-Wildcard Subdomains

Follow the process outlined in the first section above for _Non-wildcard SSL Subdomains_.

### More Topics In Multisite

*   [Multisite: Installing the Add-On](https://web.archive.org/web/20240420005750/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-installing-the-add-on/)
*   [Multisite: Introduction](https://web.archive.org/web/20240420005750/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-introduction/)
*   [Enabling Multisite](https://web.archive.org/web/20240420005750/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-multisite/)
*   [Enabling SSL For the Multisite Network](https://web.archive.org/web/20240420005750/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-ssl-for-the-multisite-network/)
*   [Add A Site To The Multisite Network](https://web.archive.org/web/20240420005750/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/add-a-site-to-the-multisite-network/)
