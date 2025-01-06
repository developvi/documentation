---
title: "Handling Multiple Sites on a Single Subscription"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Handling Multiple Sites on a Single Subscription
  parent: 10-Woocommerce
  order: 4
---
There are some instances where you might want to have your customers provision multiple sites under a single subscription. So, when when defining a product you have the option to indicate how many sites a subscription is for.

[![](https://web.archive.org/web/20240304142431im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-179.png)](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-179.png)

However, we have some limitations in how we keep track of the number of sites that are in use by a customer for a given subscription.

### Limitations

The first limitation is the process by which the user can create a new site. Generally, **we designed this entire SELL SUBSCRIPTIONS WITH WOOCOMMERCE module around the idea that one site is one subscription**. Because of this, the user cannot use the normal DVI **ADD NEW SITE** button. Instead a user will only be able to create a new site by cloning their existing site.

The second limitation is that we’ll make a good faith attempt to aggregate the number of sites that a user has purchased by increasing and decreasing a counter in the user profile. In other words, if a user purchases another subscription we will increase the count in the user profile. If they delete a site, we will decrease the count.

[![](https://web.archive.org/web/20240304142431im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-180.png)](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-180.png)

But, because we are NOT tracking the count by subscription, whenever the user cancels a subscription, the entire count is reset. _Which means that it is possible the user will not be able to clone new sites until the admin manually updates the count._

### Exceeding the Allowed Number of Sites

If a user exceeds their allowed sites, the CLONE SITE screen will simply show a message but the CLONE SITE tab will remain enabled.

[![](https://web.archive.org/web/20240304142431im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-181.png)](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-181.png)

There are certain instances where we bypass this check though:

*   If the user is an DVI Admin
*   If the user has the rights to view the server on which the site is installed (this accounts for the situation where the user might purchase both a server subscription as well as some individual site subscriptions).

Sites that are classified as staging sites are NOT included in the site count limit.

## Other

We do eventually plan to allow multiple sites per subscription and track strict limits by subscription. BUT, that is a very low priority development item since most of the use cases we have encountered so far have been one site per subscription. If you have an immediate need for multiple sites per subscription with multiple subscriptions per user tracked properly, we’re happy to consider a custom project to implement it for you.

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy WordPress Sites](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/)
*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [WooCommerce Order Processing Notes](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-order-processing-notes/)
*   [Relink A Site To A WooCommerce Order And Subscription](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/relink-a-site-to-a-woocommerce-order-and-subscription/)
*   [Use A Customer's SSH Key For Servers](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/use-a-customers-ssh-key-for-servers/)
*   [Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce](https://web.archive.org/web/20240304142431/https://wpclouddeploy.com/documentation/woocommerce/technical-notes-for-how-we-implement-templating-sites-when-selling-wp-sites-with-woocommerce/)
