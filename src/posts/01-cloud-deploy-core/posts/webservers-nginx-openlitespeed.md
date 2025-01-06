---
title: "Webservers NGINX  OpenLiteSpeed"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Webservers NGINX  OpenLiteSpeed
  parent: 01-cloud-deploy-core
  order: 7
---
DVI supports two web servers:

*   NGINX
*   OpenLiteSpeed

There are many differences between the two servers. The biggest differences are:

*   PHP versions supported
*   DVI Functions
*   Web Server Customization
*   Stability & Security

Based on these differences you might find the need to use one or the other for certain installations.

- - -

## Which Version Should You Use?

All else being equal, if you’re looking for stability and Security, use NGINX.

NGINX has the most developers working on it, orders of magnitude more installations and has been around far far longer than OLS. Many of its edge cases & security issues have been revealed and fixed.

And if something goes wrong it will be far far easier to research and find solutions as well as find engineers familiar with it.

OLS is the new kid on the block and still has teething pains. There is far less consistency in how it does things, have fewer resources to call on when researching issues and have very few engineers available who can help resolve issues. It generally will exhibit weird behavior on an ongoing basis. It is growing rapidly but still has a way to go before it can be considered fully mature and has the same level of stability and consistency as NGINX.

Additionally, OLS has been [inconsistent with how it’s handled security issues](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/multiple-high-priority-security-vulnerabilities-in-openlitespeed/) and is NOT recommended for shared servers at this time (see our note about OLS and shared servers later in this document).

- - -

## Supported PHP Versions

#### NGINX – Ubuntu 18.04

*   PHP 5.6
*   PHP 7.1
*   PHP 7.2
*   PHP 7.3
*   PHP 7.4
*   PHP 8.0
*   PHP 8.1

#### NGINX – Ubuntu 20.04

*   PHP 5.6
*   PHP 7.1
*   PHP 7.2
*   PHP 7.3
*   PHP 7.4
*   PHP 8.0
*   PHP 8.1
*   PHP 8.2

#### NGINX – Ubuntu 22.04

*   PHP 5.6
*   PHP 7.1
*   PHP 7.2
*   PHP 7.3
*   PHP 7.4
*   PHP 8.0
*   PHP 8.1
*   PHP 8.2

#### OpenLiteSpeed – Ubuntu 18.04

Not Applicable – OLS cannot be installed at all on Ubuntu 18.04

#### NGINX – Ubuntu 20.04

*   PHP 7.1
*   PHP 7.2
*   PHP 7.3
*   PHP 7.4
*   PHP 8.0
*   PHP 8.1
*   PHP 8.2

Note the absence of PHP 5.6 and PHP 7.0

#### NGINX – Ubuntu 22.04

*   PHP 7.4
*   PHP 8.0
*   PHP 8.1
*   PHP 8.2

Note the absence of support for any PHP version earlier than 7.4.

- - -

## Differences in DVI functions

The following broad areas of functions are available on NGINX servers but not OLS servers:

*   WP Multisite
*   GoAccess
*   Monitorix
*   AWStats (Command Line)
*   Crowdsec (Command Line)
*   WPScan (Command Line)

The following broad areas of functions are available on OLS servers but not NGINX servers:

*   Visual Web Server Configuration Dashboard

The following are small functional differences between NGINX and OLS servers:

#### SSL Differences

OLS will automatically handle HTTP2 when enabling and disabling SSL. NGINX requires a separate step.
For some operations, NGINX will require that HTTP2 be disabled while OLS will not have the requirement.

- - -

## Customization Differences

Using the INCLUDE functionality inherent in NGINX, we’re able to offer the admins the ability to add override directives to the DVI NGINX configuration – without directly modifying our files. This can make it easier to keep you on the upgrade path if you wish to make web server configuration changes

With OpenLiteSpeed, there is no such functionality so changes you might wish to make to your OLS server configuration will need to be done directly to the DVI OLS configuration files.

- - -

## Automatic Updates

#### NGINX

Security updates will automatically be applied for NGINX.

#### OpenLiteSpeed

Security updates will not always be automatically applied for OLS. There are two reasons for this.

1.  OLS does not always tag their security releases as such – so Linux does not always know that it should be updated as part of the security updates.
2.  OLS is notorious for releasing unstable updates. They sometimes even re-release a version with the same 3 digit version number with only the date changed!

If an OLS package is properly tagged as a security update, we will automatically apply the update using the background updates process used for all other security updates.

Unfortunately you cannot depend on OLS to always tag the updates properly. So you must periodically check and compare the OLS version you’re running with that listed on their [release pages](https://web.archive.org/web/20240529135635/https://github.com/litespeedtech/openlitespeed/releases).

You can check your OLS version by running this on the command line:

/usr/local/lsws/bin/openlitespeed -v

You can view the list of OLS versions here: [https://github.com/litespeedtech/openlitespeed/releases](https://web.archive.org/web/20240529135635/https://github.com/litespeedtech/openlitespeed/releases)

_But, as we mentioned above, sometimes a version can be re-released with a later date but it will not necessarily show up on the releases page as such. You should compare the release date with the date of the assets. If they are different then you know that fixes were snuck into a release without changing the 3 digit version number. This is how they will sneak in security updates they don’t want to fully acknowledge._

There are two ways to force an OLS update:

*   Run the following from the command line:

apt-get upgrade openlitespeed

*   You can also run all Linux updates – this you can do from the DVI **UPGRADES** tab for a server.

We hope that as the OLS product and development team matures that they start to handle security updates in the way the rest of the industry expects.

- - -

## OpenLiteSpeed on Shared Servers

We cannot recommend using OpenLiteSpeed on shared servers at this time.

The reason is because what they say about how PHP should behave is not how it actually behaves under OLS.

PHP has a number of functions that are unsafe to use on shared servers. You can turn off these functions and, in OLS, you should be able to do it on two levels – the MASTER level or the SITE level. [View more in their documentation](https://web.archive.org/web/20240529135635/https://openlitespeed.org/kb/change-php-settings-by-vhost-and-user/#Override_Global_phpini_With_Local_phpini_through_Virtual_Host_external_app).

Unfortunately, with a recent OLS update, this behavior is a bit broken. You cannot specify these functions on the site level so they have to be specified globally which affects all sites on the server.

Additionally, two functions, _proc\_open_ and _proc\_close_ cannot be restricted – otherwise WordPress sites cannot be installed. These functions can potentially give any user able to upload plugins and themes access to other areas of the server. This makes it dangerous to share multiple sites on a server with untrusted users.

Until these bugs are fixed, it is unsafe to run OLS in a shared server environment – you can only do so with containers (which DVI does not use).

If you use OLS, you need to restrict it to one site or one customer per server.

- - -

## Downgrading OpenLiteSpeed

While not recommended, you might want to do this for troubleshooting purposes.

Use this command to downgrade:

/usr/local/lsws/admin/misc/lsup.sh -v 1.7.15

Replace the **1.7.15** shown in the command above with the version number you want to downgrade to.

- - -

### More Topics In User Guide

*   [A Quick Tour](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*   [Deploy A Server](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*   [Deploy A New WordPress Site](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*   [Delete A Server](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*   [Delete A Site](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*   [Managing SSL Certificates](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*   [Page Cache](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*   [Managing sFTP Users](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*   [Cloning (Copying) Sites](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*   [Copy Site To Another Server](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*   [Copy Site To/Over Another Site](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*   [Staging Sites](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*   [Changing A Domain](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*   [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240529135635/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
