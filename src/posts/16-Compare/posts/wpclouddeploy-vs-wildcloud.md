---
title: "DevelopVIDeploy VS WildCloud (WPCS.io)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: DevelopVIDeploy VS WildCloud (WPCS.io)
  parent: 16-Compare
  order: 3
---
## What Is WildCloud (Formerly WPCS.io)

[Wildcloud](https://web.archive.org/web/20240420001926/https://wildcloud.so/) (formerly [WPCS.io](https://web.archive.org/web/20240420001926/https://wpcs.io/)) is a SaaS based service that helps you productize your WordPress sites. It does this by deploying sites in a multi-tenant architecture using serverless container technology.

The company operates out of Amsterdam, Netherlands.

The company has received investments from multiple organizations including Arches Capital Group (Amsterdam) and APX (Berlin).

## DevelopVIDeploy vs WildCloud: Similarities

Both DevelopVIDeploy & WildCloud offer solutions for deploying WordPress sites as products (SaaS) in a multi-tenant configuration.

They both offer version control, integrates with Git and make it easy to build sites with all the standard features you would expect from modern control panels:

*   Site Provisioning
*   Site cloning
*   Free SSL Certificates
*   Changing Domains
*   Staging Sites
*   Site Backups
*   Customizing webserver parameters,
*   Tracking performance
*   Integration with 3rd party services
*   WP-CLI
*   and much more…

For SaaS style products they both offer:

*   Template sites as the basis for ‘products’
*   Version controlled deployments based on template sites
*   Incremental upgrades
*   Horizontal & vertical scaling
*   Multi-tenant deployments

## DevelopVIDeploy vs WildCloud: Key Differences

The major difference between the two products is DevelopVIDeploy is a self-hosted solution while WildCloud is a 100% SaaS.

WildCloud handles the servers, containers, scaling and other back-end issues. In some ways you take what they give you though you have options to specify the size and resources used by your tenant containers.

DevelopVIDeploy is deployed on your own servers that are 100% under your control (though a sister service, [opensaas.io](https://web.archive.org/web/20240420001926/https://opensaas.io/) offers a hybrid option as well).

Additionally:

*   **DevelopVIDeploy is built on WordPress:** This makes it instantly familiar to any experienced WordPress user. And you install it the same way you install any other WordPress product extension – as a plugin.
*   **Open-source:** DevelopVIDeploy is 100% open-source and [available on Github](https://web.archive.org/web/20240420001926/https://github.com/DevelopVIDeploy) – you can see exactly what you’re installing and audit the code at any time. If security and transparency is your jam then DevelopVIDeploy is probably the tool you want to use.

## Customization Options

Since WildCloud is an SaaS service, you are locked into a fixed set of personalization options. There are likely custom services offered to assist in this area but we don’t know enough to compare them here.

Because DevelopVIDeploy is an open source product built on WordPress, the sky’s the limit when it comes to customizations and you have a lot of flexibility in how those are accomplished. You can:

*   Customize the existing code by forking it into a new codebase
*   Extend it using the WordPress extension model (plugins)
*   Combine it with other WordPress plugins

As an experienced WordPress developer or manager, you can do many of the customizations yourself. Or you can ask any other WP developer to do the work for you. Or you can ask us of course.

## Language & Locale Options

As with your customization options, WildCloud is limited in the languages and locales that can be used in their control plane without extensive customization.

DevelopVIDeploy can adopt any language you like simply by providing the translation terms using any of the many standard WP translation tools.

## Deployment Options

As with any SaaS service, your control plane is running wherever WildCloud determines is best (currently in an undisclosed AWS region.)

DevelopVIDeploy can be run on any appropriately configured server anywhere and [can be installed in multiple locations if necessary](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/deployment-scenarios-for-wpclouddeploy/). With this flexibility you can:

*   Setup a deployment or control plane for a specific set of customers.
*   Setup multiple management control planes for each legal jurisdiction in which you operate.
*   You can even build your own lite Productized WordPress service if you like.

## Server Providers

WildCloud manages all the servers and containers they use and you are not directly exposed to any of it. They currently use AWS as their provider.

DevelopVIDeploy has built-in support for 12 providers (10 public cloud providers & 2 private cloud providers) as well as the ability to “bring your own server”.

DevelopVIDeploy also has an extension toolkit where you can build your own provider. Or you can ask to have one built for you at a cost of around 3K (for providers that generally follow the openstack api style format.)

## Command Line Options

WildCloud does have a [CLI](https://web.archive.org/web/20240420001926/https://docs.wpcs.io/docs/cli/getting-started) that is based on their [API](https://web.archive.org/web/20240420001926/https://docs.wpcs.io/api).

DevelopVIDeploy uses Bash scripts that you can execute in either of two ways:

*   As a menu driven program – run the script, pick from a set of menu options and get an interactive q&a session that guides you through command completion
*   Can be run unattended by setting environment variables.

## DevelopVIDeploy vs WildCloud: Other Relevant Differences

You do not have any direct exposure to the WildCloud tech stack that is running on AWS servers and containers and you have limited customization options for it.

DevelopVIDeploy supports both a LEMP stack (Linux, NGINX, MySql/MariaDB, PHP) and a LOMP stack (Linux, OpenLiteSpeed, MySql/MariaDB, PHP). Because it’s all open source you can completely customize what is deployed in your stack.

As a SaaS service it is far easier to get started with WildCloud. DevelopVIDeploy has an installation step that can sometimes be tricky (hence our free install service when you purchase a license.)

Consistent with SaaS services, the WildCloud UI is custom-made and functional. While it can be a bit tricky, once you understand the WildCloud concepts you’ll probably love using the UI.

DevelopVIDeploy’s UI is recognizably WordPress on the backend with a highly customized UI for your end customers on the front-end.

## Pricing

Because WildCloud target market is productized WordPress (i.e.: WordPress SaaSes), we will compare only DVI prices for that same market.

WildCloud has a complex pricing structure but best we can figure out for the average site it’s going to cost between $10 and $15 per month per tenant. **There is a minimum monthly spend of $300 required to use the WildCloud service**.

DevelopVIDeploy has a flat price for its ALL ACCESS package ($999 per year) plus a minimum of $1495 for multi-tenant services in the first year. After the first year only the ALL ACCESS license is required.

At somewhere between 15 and 25 tenants (sites/customers) DVI might start to look attractive, especially if you have the technical chops to handle basic server management tasks.

WildCloud takes care of ALL server and container related issues for you so their costs are not as out-of-line as it might appear at first glance.

## Bottom Line

If you’re looking for an SaaS style product to manage your WordPress SaaS business and you’re not price conscious or you only have a small number of tenants, these folks should be first on your list. Obviously, for a self-hosted, privacy-focused, feature-packed product, choose DevelopVIDeploy.

- - -

#### Last Updated

*   _02-06-2024: Updated to include the new minimum monthly spend of $300 in the pricing section._
*   _09-23-2023: Updated to account for the name change from wpcs.io to WildCloud._
*   _Initial Cut: May 17th, 2023_

- - -

Is anything in this article incorrect? If so, please feel free to [contact us](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/cl/contact-us/) so we can apply corrections. As you might expect, corrections will be applied at our sole discretion subject to our ability to verify the new data.

- - -

### More Topics In Compare

*   [Compare DevelopVIDeploy to...](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/)
*   [DevelopVIDeploy VS GridPane](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-gridpane/)
*   [DevelopVIDeploy VS SpinupWP](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-spinupwp/)
*   [DevelopVIDeploy VS Cloudways](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-cloudways/)
*   [DevelopVIDeploy VS Runcloud](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-runcloud/)
*   [DevelopVIDeploy VS Ploi](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-ploi/)
*   [DevelopVIDeploy VS WordOps](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-wordops/)
*   [DevelopVIDeploy VS cPanel](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-cpanel/)
*   [DevelopVIDeploy VS xCloud.Host](https://web.archive.org/web/20240420001926/https://wpclouddeploy.com/documentation/compare-wpclouddeploy-to/wpclouddeploy-vs-xcloud-host/)
