---
title: "Enabling SSL For the Multisite Network"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Enabling SSL For the Multisite Network
  parent: 23-Multisite
  order: 4
---
The process for enabling SSL for your main site varies depending on the type of Multisite you have.

## Standard (Non-wildcard) SSL subdomains and Subdirectory Multisites

SSL can be enabled for the main network site by using the SSL tab.

1.  Go to WPCloud Deploy → Applications
2.  Locate your site and click on the title to navigate to the detail page
3.  Click on the _SSL_ tab
4.  Click on the SSL Status Toggle.

If the DNS for your domain is properly configured to point to your server’s IP address then a certificate will be issued and SSL will be enabled for the site.

If you get an error, check the _WPCloud Deploy->SSH LOG_ screen for a complete transcript of the action.

Important: You cannot use the SSL TAB to enable SSL for a subsite. Instead, use the SSL options under the _Multisite_ tab!

## Wildcard SSL Subdomain Multisites

SSL can be enabled under the MULTISITE tab.

1.  Go to WPCloud Deploy → Applications
2.  Locate your site and click on the title to navigate to the detail page
3.  Click on the _MULTISITE_ tab
4.  Scroll down to the _WILDCARD SSL_ section
5.  Fill out your Cloudflare data \[Note: You will need to provide a Cloudflare TOKEN, not the global API Key. Create your token here: [https://dash.cloudflare.com/profile/api-tokens](https://web.archive.org/web/20240304155344/https://dash.cloudflare.com/profile/api-tokens)\]
6.  Click on the SSL Status Toggle.

If the DNS for your domain is properly configured to point to your server’s IP address then a certificate will be issued and SSL will be enabled for the site.

If you get an error, check the _WPCloud Deploy->SSH LOG_ screen for a complete transcript of the action.

#### Notes

You can set up a special entry in the CloudFlare DNS screen to automatically route all subdomains to your Multisite install. Setup an **A** record and use “\*” as the name.

If you’re having an issue with SSL & Cloudflare make sure you disable UNDER ATTACK MODE and then try to temporarily enable DEVELOPMENT MODE.

### More Topics In Multisite

*   [Multisite: Installing the Add-On](https://web.archive.org/web/20240304155344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-installing-the-add-on/)
*   [Multisite: Introduction](https://web.archive.org/web/20240304155344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-introduction/)
*   [Enabling Multisite](https://web.archive.org/web/20240304155344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-multisite/)
*   [Add A Site To The Multisite Network](https://web.archive.org/web/20240304155344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/add-a-site-to-the-multisite-network/)
*   [Enable or Disable SSL For A Subsite On A Multisite Network](https://web.archive.org/web/20240304155344/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enable-or-disable-ssl-for-a-subsite-on-a-multisite-network/)
