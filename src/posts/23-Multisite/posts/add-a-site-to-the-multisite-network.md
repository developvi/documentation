---
title: "Add A Site To The Multisite Network"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Add A Site To The Multisite Network
  parent: 23-Multisite
  order: 5
---
The process for adding a site to the Multisite network varies depending on the type of Multisite.

## Non-wildcard SSL Subdomains

Adding a new subsite to a non-wildcard ssl subdomain multisite network is a two step process (three steps if you want to enable SSL but we’ll cover that in a separate document).

1.  Go to DevelopVIDeploy → Applications
2.  Locate your network site and click on the title to navigate to the detail page.
3.  Click on the _Multisite_ tab.
4.  Under the **Register New Subsite** section, enter the domain name – the full domain (eg: _mysudomain.maindomain.com_) but without the http:, https: or www prefixes.
5.  Click the **REGISTER** button.

This sets up the NGINX server to recognize the new subsite.

Now you just need to add the site to WordPress itself (if you haven’t already done so). Once that is complete the site has been added and is ready for use. And you can proceed to provisioning an SSL certificate for it if you so desire (see the next document for how to do this).

## Wildcard SSL Subdomains

All you need to do is setup the site inside WordPress using the normal Add Site screen. If you have a wildcard DNS entry ( “**\***” ) configured at Cloudflare then all requests for a subdomain will be routed to your Multisite automatically.

## Subdirectories

There are no special steps here – just setup the site inside WordPress using the normal Add Site screen.

Keep in mind that you cannot use mapped domains with Multisites based on subdirectories.

## Mapped Domains For Both Wildcard and Non-Wildcard Subdomains

If you are using something like WPUltimo, you can set up mapped top-level domains that route to an existing subdomain. That is, you can setup a domain such as _myexternaldomain.com_ to route to _subsite01.mymultisitedomain.com_. The user will just see _myexternaldomain.com_ in their browser – they will not know (nor do they need to know) that they are being routed to a subsite on a Multisite network.

To set this up, the process is similar to that for a new subsite under a Non-wildcard Subdomain Multisite:

1.  Go to DevelopVIDeploy → Applications
2.  Locate your network site and click on the title to navigate to the detail page.
3.  Click on the _Multisite_ tab.
4.  Under the **Register New Subsite** section, enter the domain name – the full top-level domain is needed (eg: _mydomain.com_) but without the http:, https: or www prefixes.
5.  Click the **REGISTER** button.

This sets up the NGINX server to recognize the new mapped domain and route it to the WordPress mapping handler (usually WPUltimo).

### More Topics In Multisite

*   [Multisite: Installing the Add-On](https://web.archive.org/web/20240420001040/https://developvideploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-installing-the-add-on/)
*   [Multisite: Introduction](https://web.archive.org/web/20240420001040/https://developvideploy.com/documentation/wpcloud-deploy-addons-and-upgrades/multisite-introduction/)
*   [Enabling Multisite](https://web.archive.org/web/20240420001040/https://developvideploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-multisite/)
*   [Enabling SSL For the Multisite Network](https://web.archive.org/web/20240420001040/https://developvideploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enabling-ssl-for-the-multisite-network/)
*   [Enable or Disable SSL For A Subsite On A Multisite Network](https://web.archive.org/web/20240420001040/https://developvideploy.com/documentation/wpcloud-deploy-addons-and-upgrades/enable-or-disable-ssl-for-a-subsite-on-a-multisite-network/)
