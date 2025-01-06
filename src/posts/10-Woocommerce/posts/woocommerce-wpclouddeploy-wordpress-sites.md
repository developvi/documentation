---
title: "WooCommerce & DevelopVIDeploy WordPress Sites"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WooCommerce & DevelopVIDeploy WordPress Sites
  parent: 10-Woocommerce
  order: 1
---
## Introduction

DevelopVIDeploy allows you to sell WordPress site subscriptions using WooCommerce and WooCommerce Subscriptions. With this feature it is now easier than ever create your own custom branded WP hosting service or create very sophisticated SaaS products that can scale vertically and horizontally.

To get this done you follow a simple four-step process:

1.  Decide on which servers the sites you sell should be located
2.  Optionally create “template” sites that can form the basis of your users’ new sites
3.  Optionally setup integration with Cloudflare DNS so you can automatically setup temporary domains for your customers’ sites
4.  Create subscription products in WooCommerce that are of type “WordPress Site”

As with our feature that allows you to [sell Server Subscriptions with WooCommerce](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/), customers will be able to pay with Stripe or Paypal. Other payment methods might work but they are not officially supported.

## Pre-requisites

There are a number of pre-requisites that need to be in place before you can use this feature. These are:

*   WooCommerce premium plugins
*   Overriding some default actions in WooCommerce
*   Adjusting some WooCommerce-related roles and capabilities (see more information in the next section)
*   (WooCommerce 8.3+) Create Cart & Checkout pages that uses WooCommerce shortcodes instead of blocks (see more information later below)

#### Plugins

Here are the plugins you need to make this happen (in addition to DevelopVIDeploy)

*   WooCommerce (Free)
*   [WooCommerce Subscriptions](https://web.archive.org/web/20240304151912/https://woocommerce.com/products/woocommerce-subscriptions/)
*   The WpCloudDeploy _WooCommerce_ add-on

### Servers

*   One server on which DevelopVIDeploy is installed (hopefully you already have this)
*   At least one fresh DVI server on which your customers’ sites will reside
*   Optional – one server on which you will create and store your “template sites”

- - -

## Pre-requisite: Adjust some WooCommerce-related roles and capabilities

DevelopVIDeploy offers both a front-end UI and a secure wp-admin experience. You can grant your customer one or both experiences. Most customers only require the front-end UI.

The difference between the two is that the wp-admin experience has a few functions that are rarely used by customers but if you need them, the wp-admin experience or custom code will the only two options.

If all you need your customers to do is standard WordPress admin functions such as changing domains, backups, tweaking PHP functions etc., they will not need the wp-admin experience. You can get an idea of how the front-end UI works by reading our original [Call For Testers for UI article](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/call-for-testers-front-end-ui/) from back in 2022.

If you need to grant customers access to the wp-admin area, you’ll need to handle the following items:

#### Fix WooCommerce Default Login Action

You will need a method to bypass WooCommerce’s default account page on login. WooCommerce tends to hijack the WordPress login process and send most users to the WC account area. But we want them to be able to go to our servers page instead. You can override the WC default behavior using one of the following options:

*   Turn on the option we have specifically for this under **SETTINGS → APP:WORDPRESS SETTINGS → WooCommerce Options.** This affects ALL WooCommerce users. If that’s not the behavior you want you’ll need to use one of the other options below.
*   Custom code
*   Give your users a higher level default role (not recommended)

#### Roles and Capabilities for WooCommerce Customers

You will need to grant the CUSTOMER role the following CAPABILITIES so that they can see the DevelopVIDeploy menu option in wp-admin:

*   wpcd\_manage\_servers
*   wpcd\_manage\_apps

(The CUSTOMER role is the default role that WooCommerce assigns to users who have made purchases).

You can do this with any _Roles & Capabilities_ plugin such as [User Role Editor](https://web.archive.org/web/20240304151912/https://wordpress.org/plugins/user-role-editor/).

- - -

## Pre-requisite: Create WooCommerce Cart & Checkout Pages That Use WooCommerce ShortCodes

In WooCommerce 8.3, WooCommerce replaced the shortcodes in the Cart & Checkout pages with Blocks. Unfortunately, these blocks do not have the standard WC hooks that have been around for many many years. It basically breaks functionality for a ton of plugins that modify the checkout process.

To use WooCommerce short-codes in your Cart & Checkout Pages please do the following:

*   Create a new PAGE and give it a title such as MY CART or DVI CART
*   Add in the WooCommerce CART shortcode: \[ woocommerce\_cart \]
*   Create another new PAGE and give it a title such as MY CHECKOUT PAGE or DVI CHECKOUT PAGE
*   Add in the WooCommerce CHECKOUT shortcode: \[ woocommerce\_checkout \]
*   Navigate to the WOOCOMMERCE → SETTINGS → ADVANCED tab and make sure you’re on the PAGE SETUP section (which is the default when you navigate to the ADVANCED tab).
*   Replace the CART PAGE and CHECKOUT PAGE settings with your custom pages created earlier
*   Scroll down click the SAVE CHANGES button
*   Navigate to the wordpress SETTINGS → PERMALINKS screen
*   Click the SAVE CHANGES button to update permalinks

- - -

## Setup Servers

There are two ways to tell DVI where your new customers’ sites should be located:

*   Select servers in the **WpCloudDeploy → SETTINGS** screen or
*   Specify ONE server for each product at the time you create the product.

You can also do a mix – create some products that use the servers from the **WpCloudDeploy → SETTINGS** screen and some that use a directed server at the time you create the product.

To select servers in the SETTINGS screen:

*   Go to **WpCloudDeploy → SETTINGS → APP:WordPress Settings**
*   Click on the **SELL WP SITES WITH WOOCOMMERCE** tab.
*   The first section of the resulting screen will be a list of your servers – just check off the ones you want to use. (As servers fill up you can remove them and add new ones so your initial choices aren’t fixed.)
*   Click the **SAVE** button at the bottom of the screen.

[![](https://web.archive.org/web/20240304151912im_/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-13.png)](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-13.png)

- - -

## Setup Cloudflare DNS Integration

When your customers purchase a site from you, we need to assign it a temporary domain. You can choose to have this domain automatically set up in Cloudflare. Here is how you do both of these things:

1.  Specify the root of your temporary domain (xxx.yyy) in the **WpCloudDeploy → SETTINGS → APP:WordPress Settings → SELL WP SITES WITH WOOCOMMERCE** tab.
2.  On that same screen, there is a section called **AUTOMATIC DNS VIA CLOUDFLARE** – fill out that form with your **ZONE ID** for the root domain you specified in step 1 above and your CloudFlare security token. (Obviously Cloudflare must be the authoritative name servers for your domain).
3.  Click the **SAVE** button.

[![](https://web.archive.org/web/20240304151912im_/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-15.png)](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-15.png)

- - -

## Configure Products

Configuring your WordPress Site products is easy – just use the standard WooCommerce Product screen.

*   Products must be of type **SIMPLE SUBSCRIPTION**
*   The checkbox for **THIS IS A WORDPRESS SITE** located under the **WORDPRESS SITES** tab must be turned on.
*   Click on the _Inventory_ tab to enable stock management – turn on the option for _Sold Individually_.
*   In most cases you would want to check the **VIRTUAL** option as well since it’s not something that is being shipped.

[![](https://web.archive.org/web/20240304151912im_/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-16.png)](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/wp-content/uploads/2021/01/wpcd-wc-16.png)

- - -

## Remove Ajax Buttons

If you’ll be using the WC product archive pages, you must remove the AJAX buttons because they bypass the product detail page. The product detail page is where the customer choose their site options.

One way to disable these buttons is via CSS such as the following (your theme might have slightly different classes):

.archive .add\_to\_cart\_button {
display: none; !important
}

- - -

## Template Sites

Template sites allow you to create sites to use as the baseline for new sites. So, when your customer purchases a site product from your WooCommerce store they can start with the template you specify.

Template sites must be placed on their own server – they cannot be on the same server where your customer sites are being deployed.

This means that to use template sites you need a minimum of two servers – one for the template sites and one for your customer sites (plus a third server for your DVI site).

You can designate any site as a template site on any server – as long as it’s not on the same server as where your customers’ new site(s) will be deployed.

To designate a site as a template site just use the checkbox in the SITE DETAILS screen:

[![](https://web.archive.org/web/20240304151912im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-56-wc-template-settings-02.png)](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-56-wc-template-settings-02.png)

- - -

## Product Packages

Product Packages (aka Site Packages, aka blueprints) allow you to configure resources, plugins and themes for each plan or product.

Learn more about this feature in our release article: [Product Packages for WooCommerce](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/introducing-product-packages-for-our-woocommerce-integration/)

- - -

## Advanced Features

- - -

The WooCommerce integration module includes a number of additional features not discussed above. These include:

*   Cancellation options – lock or disable sites
*   Options for handling sites when subscriptions are placed on hold
*   Subscription switching
*   Suppressing certain emails
*   Custom emails per product

Learn more about these features in our [DVI WooCommerce 3.0 document](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/whats-new-in-wpcd-woocommerce-3-0/).

- - -

## Automatically Expiring Sites

You can setup ‘temporary’ products that auto-expire after a period of time. Learn more about these in the [Site Expiration documentation](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/) – scroll down to the WooCommerce section towards the end of the document.

- - -

## Quotas for Custom Post Types

You can create product plans that enforce quotas on custom post types (pages, posts, attachments etc.) Learn more about this feature in the [Custom Post Type Quotas documentation](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/).

- - -

## Useful Filter Hooks

apply\_filters( "wpcd\_wpapp\_wc\_validate\_domain\_on\_checkout", true, $domain, $domain\_root )

Use this filter to validate the domain. For example you can use it to check that it does not include rude words in your language. Return false to stop the checkout process or true to allow checkout to continue.

This hook only apply after it passes all our validations. You cannot use it to override our internal validations. You can use it only to layer in your own additional validations.

apply\_filters( "wpcd\_wpapp\_wc\_validate\_password\_on\_checkout", true, $pw )

Use this filter to validate the password. For example you can use it to check that it contains a minimum number of characters. Return false to stop the checkout process or true to allow checkout to continue.

This hook only apply after it passes all our validations. You cannot use it to override our own validations. You can use it only to layer in your own additional validations.

apply\_filters( "wpcd\_wc\_checkout\_site\_name\_desc", '' )

Use this filter to set a description for the site name / domain on the checkout page.

apply\_filters( "wpcd\_wc\_checkout\_site\_password\_label", '' )

Use this filter to set a description for the password on the checkout page – only use this if you’re turned on the password field on the checkout page.

- - -

## Important Notes & Limitations

### Configuring Target Servers

We strongly recommend that each of your target servers install the SMTP gateway. Otherwise your users will not be able to get a password reset email to log into their new sites. A side effect of this though is that a malicious user can use their WordPress site to send out spam emails which will cause the servers’ ip address to be blacklisted. So definitely make an effort to know your customer.

An alternative to this is to send your customers their passwords in the confirmation email – less secure but it might not matter if you are creating relatively simple sites.

### Some Limitations

This function is not designed for you to sell dozens of WordPress subscriptions an hour. We have not tested it with more than a few sites every hour. So officially, we are stating that it will not work well if you’re provisioning more than one site every 10 minutes on the same target server. (Though, while we suspect that you can do more than that, we just don’t want you trying to sell 100 sites every 10 minutes).

We do have a higher priced solution suitable for high volume agencies So, if you need high-volume provisioning please contact us and we’ll provide a quote to get this up and running for you.

### Canceling Multiple Subscriptions

WooCommerce allows you to cancel multiple subscriptions at a time from its subscriptions list. However, keep in mind that each subscription has to then reach out to the WordPress servers and remove the associated sites. So it’s best to bulk cancel only 4 or less at a time. Otherwise, the PHP script will timeout and things will be left in an unknown state.

### Delete Protection Limitations

Sites have a flag that allow users and admins to remove the DELETE option from the screen. This prevents accidental deletion of the site from the UI. However, when a subscription is canceled the associated site is deleted regardless of this value.

### Add-To-Cart & Checkout Notes

You must LIMIT the number of sites that can be ordered at the same time to ONE. We have attempted to do that for you but you can ensure that this limitation is adhered to by doing the following when setting up your product:

*   Click on the _Inventory_ tab to enable stock management – turn on the option for _Sold Individually_.

### Using Template Sites

Azure, GCP & Alibaba servers should not be used when using Template Sites. In other words, you should not set up a product where the destination server is located at one of these providers AND there is a template site that needs to be used for the new site. However, you can still use these providers for sites without templates.

The reason that this is a limitation is because we need full ‘root’ access to set up the processes on both servers that make copying sites efficient. So any server that does not use ‘root’ as the login cannot be used for template or target sites.

### Bulk Actions In The WC Subscriptions List

Most BULK actions will not properly handle cancelling sites. The only ones that will properly delete sites is CANCEL. Others such as “Move To Trash” will not do it.

And, “ACTIVATE” will not create a new site! So if a subscription was put on hold or somehow did not complete properly during initial checkout, the ACTIVATE function will not create the new site!

In general, please be careful using WooCommerce BULK ACTIONS with subscriptions and orders that involve DVI related functionality.

- - -

## FAQ: Template Sites VS WPUltimo

Before this product has even been released we have had discussions with users where this question was raised – in fact it was the number one question for this feature. So we’re going to address it here in the documentation (and possibly elsewhere on our site) in as much gory detail as we can muster.

_Selling WP Site Subscriptions With WooCommerce_ is a much different experience than WPUltimo. WPUltimo will be far easier to get started with and can be used with most hosts. DVI’s _Selling WP Site Subscriptions With WooCommerce_ can only be done by managing your own servers with the DVI Plugin. And it requires a higher level of skill to get started.

From a cost standpoint, you can get started with WPUltimo for under $500 dollars including hosting. With DVI, you’ll need the $999 plan plus three small cloud servers plus WooCommerce and WooCommerce subscriptions. And you will need some sort of dedicated central site management tool such as MainWP or ManageWP. So you’ll be out over $1300 before you even bring up your first site.

From a skills standpoint you can use WPUltimo with beginner WP skills. You cannot do that with DVI. In fact, DVI is targeted at users with at least 1 year of solid WP experience who are looking to level up their skills – and their WP hosting options.

With WPUltimo you can go to almost any WordPress hosting company, install it and get started with it in about 30 minutes.

With DVI you have to:

*   Install it on a server
*   Install WooCommerce
*   Install WooCommerce subscriptions
*   Generate SSH keys
*   Connect to a cloud server provider
*   Fire up a couple of cloud servers

All before you can create your first product.

**After reading all that, you are probably thinking “What the heck? Are they trying to turn me off of DVI and go to WPUltimo?”**

No, not at all. There is definitely overlap between our _WooCommerce_ feature and WPUltimo. But only in some areas. In other areas, DVI is a far more expansive and ambitious product than WPUltimo.

While you pay a higher price in both dollars and skills with DVI you get a LOT in return! Some benefits are:

*   You can scale your WaaS horizontally and vertically.
*   Your WaaS project can use many more plugins – many of which will not run on a Multisite. In particular you can now build out WaaS services that use WooCommerce.
*   By distributing your WaaS sites across many servers and server providers you can prevent all your customers from suffering from an outage at the same time – no more risking 50+ irate customers because you made a mistake on your WP Multisite install.
*   You can do rolling updates – testing new features on some customers first to make sure there are no side-effects before rolling them out to your entire customer base.
*   You can easily increase resources for those customers who need it without having to scale for ALL your customers at the same time – not all customers are created the same!
*   You can use plugins that are problematic on Multisite such as WooCommerce.
*   If you service customers from around the world you can choose servers closest to their geographic region which can make their sites feel faster for their customers.
*   You can offer customers additional purchase options for using plugins that might not have been possible on a dedicated Multisite installation.
*   If you are unfortunate enough to suffer a malware infection, it will likely affect only the few customers on a server rather than all your customers the way it would on a Multisite installation.
*   You can use WP Site management panels such as MAINWP and MANAGEWP to managed your sites at scale. These panels do not officially support Multisite installations of WP.

I think you get the point. You pay a higher price for a LOT of benefits. But you do have to forego some of the WPUltimo conveniences.

So, you just have to decide what’s important to you and how you prefer to work. Neither option is the “best” for everyone. And we don’t view ourselves as WPUltimo competitors – in fact we use them for some of our own projects! And, if you want, I suspect you can find a way to sell WPULTIMO multi-sites on DVI! Now ain’t that something?

- - -

## Resources

[How To Build a WordPress SaaS (Video Course)](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/how-to-build-a-wordpress-saas-video-course-free/)

- - -

## Related Articles

[Introducing Product Packages For our WooCommerce Integration](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/introducing-product-packages-for-our-woocommerce-integration/)

[What’s New In DVI WooCommerce 3.0](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/whats-new-in-wpcd-woocommerce-3-0/)

[Sell Site Subscriptions With WooCommerce V1.5](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/sell-site-subscriptions-with-woocommerce-v1-5/)

[All Articles Tagged with ‘WooCommerce’](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/tag/woocommerce/)

- - -

## Related Sites

*   [opensaas.io](https://web.archive.org/web/20240304151912/https://opensaas.io/)
*   [wpcd.cloud](https://web.archive.org/web/20240304151912/https://wpcd.cloud/)

- - -

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [WooCommerce Order Processing Notes](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-order-processing-notes/)
*   [Handling Multiple Sites on a Single Subscription](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/handling-multiple-sites-on-a-single-subscription/)
*   [Relink A Site To A WooCommerce Order And Subscription](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/relink-a-site-to-a-woocommerce-order-and-subscription/)
*   [Use A Customer's SSH Key For Servers](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/use-a-customers-ssh-key-for-servers/)
*   [Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce](https://web.archive.org/web/20240304151912/https://wpclouddeploy.com/documentation/woocommerce/technical-notes-for-how-we-implement-templating-sites-when-selling-wp-sites-with-woocommerce/)
