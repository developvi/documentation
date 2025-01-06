---
title: "DevelopVIDeploy VS Cloudways"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: DevelopVIDeploy VS Cloudways
  parent: 16-Compare
  order: 5
---
## What Is Cloudways

Cloudways is a SaaS service where you can deploy and manage Linux servers for a variety of tech stacks, including WordPress. It provisions servers at many of the large cloud server providers including AWS, GOOGLE, DIGITALOCEAN, LINODE & VULTR. However, these servers are not under your control – if you leave the service, you cannot take the servers with you.

The company itself is located in Malta.

## DevelopVIDeploy VS Cloudways: Similarities

Both DevelopVIDeploy and Cloudways allow you to deploy and manage WordPress servers. All the key WordPress management tools are available in both offerings including:

*   Server Provisioning
*   Site Provisioning
*   Site cloning
*   Free SSL Certificates via LetsEncrypt
*   Changing Domains
*   Staging Sites
*   Site Backups
*   and much more…

## DevelopVIDeploy VS Cloudways: Key Differences

There are four key differences between DevelopVIDeploy and Cloudways:

1.  **DevelopVIDeploy is a self-hosted product:** While Cloudways is hosted and managed in the “cloud’ on your behalf, you run DevelopVIDeploy on your own servers. This means that no staff member at DevelopVIDeploy will ever have access to your servers and sites unless you affirmatively grant them that access via a support request.
2.  **DevelopVIDeploy is built on WordPress:** This makes it instantly familiar to any experienced WordPress user. And you install it the same way you install any other WordPress product extension – as a plugin.
3.  **SaaS Builder Features:** Cloudways does not have many features that are specifically geared towards helping SaaS builders develop, configure, deploy and manage a SaaS on WordPress. DevelopVIDeploy has many features that were developed specifically in response to the needs of SaaS builders – for example, tight WooCommerce integration, Site Update Packages, multiple deployment options (standard sites and multi-tenant sites) etc.
4.  **Open-source:** DevelopVIDeploy is 100% open-source and [available on Github](https://web.archive.org/web/20240420001126/https://github.com/DevelopVIDeploy) – you can see exactly what you’re installing and audit the code at any time. If security and transparency is your jam then DevelopVIDeploy is probably the tool you want to use.

## Customization Options

Since Cloudways is an SaaS service, you are locked into a fixed set of personalization options. We do not know if they entertain requests for customization.

Because DevelopVIDeploy is an open source product built on WordPress, the sky’s the limit when it comes to customizations and you have a lot of flexibility in how those are accomplished. You can:

*   Customize the existing code by forking it into a new codebase
*   Extend it using the WordPress extension model (plugins)
*   Combine it with other WordPress plugins

As an experienced WordPress developer or manager, you can do many of the customizations yourself. Or you can ask any other WP developer to do the work for you. Or you can ask us of course.

## Language & Locale Options

As with your customization options, Cloudways is limited in the languages that can be used.

DevelopVIDeploy can adopt any language you like simply by providing the translation terms using any of the many standard WP translation tools.

## Deployment Options

As with any SaaS service, your dashboard is running wherever Cloudways determines is best.

DevelopVIDeploy can be run on any appropriately configured server anywhere and [can be installed in multiple locations if necessary](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/deployment-scenarios-for-wpclouddeploy/). With this flexibility you can:

*   Setup a dashboard for a specific set of customers.
*   Setup multiple management dashboards for each legal jurisdiction in which you operate.
*   Even build your own “Cloudways” lite service for WordPress if you like.

## Server Providers

Cloudways has direct support for three server providers plus the ability to bring your own server. (They used to support five but dropped support for Cloudways and Linode after DigitalOcean acquired them.)

DevelopVIDeploy has built-in support for 12 providers (10 public cloud providers & 2 private cloud providers) as well as ability to “bring your own server”.

DevelopVIDeploy also has an extension toolkit where you can build your own provider. Or you can ask to have one built for you at a cost of around 3K (for providers that generally follow the openstack api style format.)

## Command Line Options

Cloudways does not have a command line option. But you can ssh into your server and perform some management tasks including using WP-CLI.

DevelopVIDeploy uses Bash scripts that you can execute in either of two ways:

*   As a menu driven program – run the script, pick from a set of menu options and get an interactive q&a session that guides you through command completion
*   Can be run unattended by setting environment variables

## DevelopVIDeploy VS Cloudways: Other Relevant Differences

Sites deployed on Cloudways uses a LEMP stack with a customized Caching plugin (they call it Breeze.) However, because their servers are designed to run multiple types of services (not just WordPress) the stack is not fully optimized for WordPress.

DevelopVIDeploy supports both a LEMP stack (Linux, NGINX, MySql/MariaDB, PHP) and a LOMP stack (Linux, OpenLiteSpeed, MySql/MariaDB, PHP).

As an SaaS service it is far easier to get started with Cloudways. DevelopVIDeploy has an installation step that can sometimes be tricky (hence our free install service when you purchase a license.)

Consistent with SaaS services, the Cloudways UI is custom-made highly functional, with many micro-interactions. DevelopVIDeploy’s UI is recognizably WordPress on the backend with a highly customized UI for your end customers on the front-end.

## Pricing

Cloudways make their money by adding a markup to each server you provision. For example, if you choose to use a $5 server from DigitalOcean they will charge you $10. The more servers you deploy, the higher your monthly bill.

DevelopVIDeploy charges a single annual fee or lifetime fee with no per-server or per-site limits. You have three levels to choose from based on the functionality you need.

## Converting From Cloudways to DevelopVIDeploy

You can transfer your sites using any WordPress backup tool. We recommend UPDRAFT PLUS though many folks seem to prefer using DUPLICATOR PRO (something we’re far less familiar with).

## Other

The above summary is only focused on the product differences and similarities. There are, of course, differences between the companies themselves – including large differences in operations, pricing, support policies, affiliate programs and more.

## Bottom Line

If you’re looking for an SaaS style product to manage your WordPress business you should look at GridPane or SpinpupWP – unless you have other product stacks you need to support. Obviously, for a self-hosted, privacy-focused, feature-packed product, choose DevelopVIDeploy.

- - -

#### Last Updated

*   _May 8th, 2022: Added note about the reduced number of providers that are supported_
*   _October 11th, 2022: Minor updates to note DVI OpenLiteSpeed support, new providers + grammer clean up._
*   _June 3rd, 2022_

- - -

Is anything in this article incorrect? If so, please feel free to [contact us](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/cl/contact-us/) so we can apply corrections. As you might expect, corrections will be applied at our sole discretion subject to our ability to verify the new data.

- - -

### More Topics In Compare

*   [Compare DevelopVIDeploy to...](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/)
*   [DevelopVIDeploy VS GridPane](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-gridpane/)
*   [DevelopVIDeploy VS WildCloud (WPCS.io)](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-wildcloud/)
*   [DevelopVIDeploy VS SpinupWP](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-spinupwp/)
*   [DevelopVIDeploy VS Runcloud](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-runcloud/)
*   [DevelopVIDeploy VS Ploi](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-ploi/)
*   [DevelopVIDeploy VS WordOps](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-wordops/)
*   [DevelopVIDeploy VS cPanel](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-cpanel/)
*   [DevelopVIDeploy VS xCloud.Host](https://web.archive.org/web/20240420001126/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-xcloud-host/)
