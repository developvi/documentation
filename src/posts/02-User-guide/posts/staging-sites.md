---
title: "Staging Sites"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Staging Sites
  parent: 02-User-guide
  order: 12
---
Staging sites in DVI work a little differently when compared to your traditional hosts like WPEngine, Cloudways etc. Behind the scenes we treat staging sites the same as regular sites.

There are two ways to create staging sites in DVI:

*  Simplified – this method is close to the process you’ll see at traditional hosting services.
*  Advanced – this method allows you to have as many staging sites as like.

- - -

## Simplified Staging Sites

If you configure your DNS settings for CloudFlare you can gain access to one-click staging site functionality.

You configure DNS Integration with CloudFlare under the DevelopVIDeploy → SETTINGS → WORDPRESS SETTINGS → DNS: CLOUDFLARE tab.

Once that integration has been configured, you can create a staging site under the STAGING tab for a site.

[![](https://web.archive.org/web/20240304160247im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-176.png)](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-176.png)

This tab will have a single button on it depending on context.

[![](https://web.archive.org/web/20240304160247im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-177.png)](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-177.png)

If a site is not a staging site, the button will offer the option to either:

1.  Create a new staging site (which uses our CLONE SITE functionality behind the scenes or)
2.  Overwrite any existing staging site (which uses our [COPY TO EXISTING SITE function](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/) behind the scenes.)

If a site is already tagged as a staging site, it will just offer the option to push back to live. As you might expect, this “push to live” feature just uses our existing COPY TO EXISTING SITE functionality.

With Simplified Staging Sites there is a pre-defined, one-to-one relationship between a live site and the staging site.

Simplified Staging Sites have a special tag on them that identifies them as such. This means that you can assign different permission levels to them vs the live site – see the DevelopVIDeploy → SETTINGS → WORDPRESS SECURITY → STAGING SITES tabs.

- - -

## Advanced Staging Sites

The primary reason that traditional hosts treat staging sites differently is to prevent you from using them as regular sites. If you purchase a 2-site hosting plan, they don’t want you to end up with 4 live sites.

With DVI, it’s your server so there’s no need to make that artificial distinction between staging sites and live sites. Additionally, with Advanced Staging sites you can create as many staging sites as you like – most traditional hosts will only allow one staging site for each live site in your service plan.

The process for creating an ‘advanced’ staging site is as follows:

1.  [Clone an existing site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
2.  (Optional) [password-protect the new site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/).
3.  (Recommended) Disable or clear caches on the new staging site

When it’s time to push the staging site back to the live site you use the [Copy To Existing Site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site) feature.

DVI staging sites usually live on the same server as your live site. However, you can create a staging site on a different server if you so choose. But to copy a staging site back over to a live site that is located on a different server you’ll need to follow a multi-step process:

1.  Clone the staging site to another site on the same server on which it resides – this is VERY important because this changes the database name. **If you do not perform this step then you will corrupt the live site on the target server!**
2.  [Copy the cloned staging site to the same server as the live site.](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/) Please make sure that you use the cloned staging site from step 1 for for this part of the operation – otherwise you will corrupt the live site on the target server!
3.  Use the [Copy To Existing Site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site) feature after the staging site has been copied to the same server as the target site

- - -

## Notes

When you push a staging site back to the live site, there are usually clean-up tasks that you need to perform. Some of these include:

*  Clearing caches
*  Re-creating or deleting caches used by page-builders, themes and some plugins
*  Resetting permalinks

Please keep these additional items in mind:

*  A staging site starts with a new default VHOST configuration file. This means that items such as 7G/6G, tweaks, web-server redirects and HTTP AUTH are NOT copied to the new site.
*  Staging sites do not inherit backup configurations
*  Staging sites do not inherit the LINUX CRON setting – the sites default back to the core WordPress CRON process.

## Tips

*  Consider creating a DVI extension to run your own bash script after creating a staging site and/or after copying back to live. This script can automate some of the after-push actions mentioned above that are unique to you.

- - -

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Changing A Domain](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240304160247/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
