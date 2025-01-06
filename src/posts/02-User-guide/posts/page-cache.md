---
title: "Page Cache"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Page Cache
  parent: 02-User-guide
  order: 7
---
## Introduction

WordPress is a PHP application which means that every request for a page or resource requires a compilation step. This dramatically increases the response time and adds substantial load to the server. But, most pages and resources are static or do not often change. This means that once the page or resource has been compiled, it can be stored so that the next request does not require the compilation step.

The feature that implements this idea is called a “Page Cache”. Almost every WordPress host you’ve ever used provides some sort of ability to enable a page caching service. Most use an NGINIX based page cache, a REDIS page cache, a VARNISH based page cache or a proprietary page cache. But they all aim to do the same thing – store a pre-compiled WordPress page or object so that it can be served much faster.

The DevelopVIDeploy Plugin uses either an NGINX based page cache or the native OpenLiteSpeed server page cache, depending on which webserver is in use.

## NGINX Web Servers

The DevelopVIDeploy Plugin uses the NGINX web server to manage a WordPress page cache. In order to do this, it requires a WordPress plugin called CACHE ENABLER (published by KEY CDN). When you enable the page cache in the DevelopVIDeploy admin area, the plugin is automatically installed and enabled.

The plugin automatically generates and places pages into the page cache folder which NGINX first checks before serving up a page.

The following pages are automatically excluded from the cache:

*  Any page with data from forms
*  URLS with query data strings
*  Pages served when the user is logged in.

The Cache-Enabler plugin for NGINX stores cache files in the following location:

/var/www/myblog.com/html/wp-content/cache/cache-enabler/

#### Why NGINX?

There are many ways to handle a page cache. A couple we have already mentioned: REDIS & VARNISH. We decided not to use any of those simply because we’re already using NGINX and NGINX can already make very efficient use a cache – if one is set up. This greatly reduces the complexity of the tech stack as well as reduces the memory in use and removes another potential point of failure where things can go wrong.

- - -

## OpenLiteSpeed Web Servers

When using an OpenLiteSpeed web server, we use the built-in OpenLiteSpeed page cache along with the OpenLiteSpeed WordPress plugin.

You can access all the OpenLiteSpeed cache options from inside each website under the **LiteSpeed Cache** item in the WordPress wp-admin menu bar.

- - -

## Caching And WordPress Crons

WordPress fires off its scheduled activities (‘cron’) only when a site has traffic. In other words, when WordPress is called to load a page or post, it also checks to see what other activities are in the scheduler that also needs to be completed. If WordPress isn’t called to load a page, scheduled activities are not run.

When a page is cached, WordPress is never called. Which means that some scheduled activities might be delayed or not get run at all.

So, if you’re using a page cache and you expect most of your site requests to be served from the cache, we recommend that you turn on the LINUX based cron process – you can do this from the _CRON_ tab on your site.

- - -

## Turning On The Page Cache

The page cache is enabled by default on new sites. But, if for some reason it’s turned off (eg: you might have imported a site), you can turn it on as follows:

1.  Go to DevelopVIDeploy → Applications
2.  Click on the site where you need to turn on the page cache
3.  Click on the _Cache_ tab
4.  Scroll down to the _PAGE CACHE_ section
5.  Click on the toggle switch

If you are using an NGINX web server you can verify that the cache is turned on by viewing the source code for a page in a browser. At the very bottom of the page code you should see something that looks like this:

<!-- Cache Enabler by KeyCDN @ 07.02.2021 00:13:37 (https html) -->

If you do not see this then either the page is not cacheable or we were unable to add a required entry to your wp-config.php file. Open your wp-config.php and verify that this entry exists:

define( 'WP\_CACHE', 'true' );

It might be wrapped in a conditional such as:

if ( ! defined( 'WP\_CACHE' ) ) {
define( 'WP\_CACHE', 'true' );
}

If you do not see it then you should add it!

## Clearing The Page Cache

There are times when you need to clear the cache so that it can be rebuilt. To do this:

1.  Go to DevelopVIDeploy → Applications
2.  Click on the site where you need to turn on the page cache
3.  Click on the _Cache_ tab
4.  Scroll down to the _PAGE CACHE_ section
5.  Click on the _Clea_r button

## Add Exceptions To The Page Cache

#### Nginx Web Server

Exceptions need to be added from your sites’ WordPress dashboard, not the DevelopVIDeploy dashboard.

1.  Go to your WordPress sites’ Settings → Cache Enabler screen in wp-admin
2.  Fill in the items as necessary
3.  Click the _Save Changes_ button.

#### OpenLiteSpeed Web Server

1.  Go to your WordPress sites’ LiteSpeedCache → Cache screen in wp-admin
2.  Click on the EXCLUDES tab
3.  Fill in the items as necessary
4.  Click the _Save Changes_ button.

- - -

## Availability

The OpenLiteSpeed Web Server cache options are only available in DVI V 5.0.0 or later.

- - -

- - -

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Managing sFTP Users](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240529160437/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
