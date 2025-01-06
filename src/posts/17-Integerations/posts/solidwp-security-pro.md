---
title: "SolidWP Security Pro"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: SolidWP Security Pro
  parent: 17-Integerations
  order: 3
---

[SolidWP Security Pro](https://web.archive.org/web/20240304161513/https://solidwp.com/security/) is a security plugin that offers quite a number of features. The product used to be called ‘iThemes Security Pro’ and internally, the code still refers to that name.

These days, the product is all grown up and includes a huge number of security features that make it competitive with other security plugins.

We are able to integrate it cleanly into DevelopVIDeploy because it offers a [comprehensive WP-CLI interface](https://web.archive.org/web/20240304161513/https://help.solidwp.com/hc/en-us/articles/204289604-Solid-Security-WP-CLI-Integration).

And, the pricing is pretty reasonable, especially for agencies – 25 sites is $399 per year (less than $20 per site per year). Compare that to something like WordFence where 25 sites will cost you north of $2300.

Solid Security Pro includes all the features you would expect in a modern security Plugin:

*   Scanner
*   Brute-force attack prevention
*   File change detection
*   Notifications
*   2FA
*   Passkeys

## Using the SolidWP Security Pro DevelopVIDeploy Integration

Before you can use SolidWP Security Pro with DevelopVIDeploy you need to add three pieces of information to the global settings:

*   Navigate to the **WpCloudDeploy → SETTINGS → APP: WORDPRESS – SETTINGS → INTEGRATIONS** tab
*   Scroll down tot he **SOLIDWP SECURITY** section
*   Enter your SolidWP account user name and password.
*   In the **SOLIDWP FILE URL** field you need to enter a location for the SolidWP Pro zip file. This needs to be a URL that starts with HTTPS://.
*   Optionally check the ENABLE BULK ACTIONS checkbox – this will allow you to easily add SolidWP Pro to your existing sites using the WordPress BULK ACTIONS menu in the sites list
*   Scroll down to the bottom and click the **SAVE SETTINGS** button

## Add SolidWP Security Pro To An Existing Site

To add SolidWP Security Pro to an existing site:

*   Navigate to the **WpCloudDeploy → ALL APPS** list
*   Scroll down to the site you want to work with and click on the TITLE link to bring up the site details screen
*   Click on the **SECURITY PLUGIN** tab
*   Click the switch

After a while you should get a success message.

## Add SolidWP Security Pro To All New Sites

You can automatically add SolidWP Security Pro to all new sites as follows:

*   Navigate to the **WpCloudDeploy → SETTINGS → APP: WORDPRESS – SETTINGS → SITES** tab
*   In the **SITE SETUP OPTIONS** section, enable the **ACTIVATE SOLID SECURITY PRO** checkbox
*   Scroll down to the bottom and click the **SAVE SETTINGS** button

[![](https://web.archive.org/web/20240304161513im_/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-solidwp-02.png)](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-solidwp-02.png)

Now, every time you create a new site SolidWP Security Pro will automatically be activated and licensed for it.

A few things to keep in mind:

*   On a brand new site you’ll still need to log in and follow the setup wizard to get things fully activated and configured.
*   If you create a new site and then import a site over it, the SolidWP Security connection will disappear because the SolidWP Security plugin and data will no longer be there. You will need to follow the steps listed in the **Add SolidWP Security Pro To An Existing Site** above to re-connect the site.
*   Deleting a site from DevelopVIDeploy does NOT delete the site from the SolidWP Security License Dashboard. To prevent charges for non-existent sites you should delete the site directly from the SolidWP Security dashboard.

- - -

## Using SolidWP Security Pro With Site & Product Packages

You can enable SolidWP Security Pro for any site that uses a site package. Just go to the **Site Package** (or **Product Package**) screen and enable the SolidWP Security Option.

[![](https://web.archive.org/web/20240304161513im_/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-site-packages-05.png)](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-site-packages-05.png)

This is best used in a SaaS and template sites. The idea is that you would have configured SolidWP Security Pro in the template site and deactivated the plugin there. Then, on new tenant/customer sites it will be activated and licensed for that domain.

- - -

## Using SolidWP Security Pro With Site Update Packages

If you have a lot of existing sites that are part of a SaaS, you can push out an update to them that automatically enables SolidWP Security Pro.

Just go to the **Site Update Packages** screen and enable the SolidWP Security option there:

[![](https://web.archive.org/web/20240304161513im_/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-site-update-packages-02.png)](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/wp-content/uploads/2023/11/wpcd-56-site-update-packages-02.png)

This is most useful if you have a set of existing sites to which you need to add SolidWP Security. But you’ll still need to log in and configure each site individually if they’ve never been configured on those sites before.

- - -

## Notes

This integration is with the SOLIDWP SECURITY **PRO** plugin – not the free plugin. The special sauce here is the automatic licensing and integration with the SolidWP license/SaaS dashboard. Without the license the plugin will not receive updates or the latest security signatures for use with the scanner.

If you’d like to use the free plugin you can use SITE PACKAGES to automatically add it to new sites or SITE UPDATE PLANS to push it to existing sites – no license key is necessary for it.

We would like to mention that a security plugin is no a panacea for good security practices. **Good security is done in layers** – by the time traffic hits your site, most of the bad stuff should already be filtered out by a proxy such as CloudFlare, a server level firewall such as UFW and a web-server level firewall such as the 7G firewall.

- - -

### More Topics In Integrations

*   [DevelopVIDeploy Integrations](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/documentation/integrations/wpclouddeploy-integrations/)
*   [Logtivity](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/documentation/integrations/logtivity/)
*   [HTMLcssToImage](https://web.archive.org/web/20240304161513/https://wpclouddeploy.com/documentation/integrations/htmlcsstoimage/)
