---
title: "WooCommerce Order Processing Notes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WooCommerce Order Processing Notes
  parent: 10-Woocommerce
  order: 3
---
A WooCommerce order goes through a number of different processing statuses throughout it’s lifecycle.

[![](https://web.archive.org/web/20240304144054im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/woocommerce-orderprocess-status-sequence.png)](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/wp-content/uploads/2022/07/woocommerce-orderprocess-status-sequence.png)

We perform different actions at each stage of the cycle as follows:

*   **Processing**: We create the server or site
*   **Cancelled**: We DELETE the server. For sites we either delete it or mark it for deletion while disabling it or password protecting it – you can set your choices in our SETTINGS area.
*   **Refunded**: We do nothing.

After PROCESSING is completed, we set the status of the order to COMPLETED. If you do not want the order to be set to COMPLETED, there are options in the settings area to disable this function.

_Important Note: We have seen 3rd party WooCommerce plugins that will hook into the order COMPLETED state and never return a value from that hook. T**his is a bug in those plugins and violates all kinds of WordPress expectations around how hooks should behave**. The end result is that this will cause some of DVI’s code to not execute, leaving some DVI things in an indeterminate state. If you see or suspect this is happening, you should choose the option inside DVI SETTINGS to NOT complete the order. You can later complete the order manually if needed._

### Refunds

As noted above, we do nothing if the order is refunded. This means you’ll need to cancel the subscription yourself if you need the subscription cancelled and sites / servers deleted.

## Additional References

[WooCommerce Subscription Action Reference](https://web.archive.org/web/20240304144054/https://woo.com/document/subscriptions/develop/action-reference/)

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy WordPress Sites](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/)
*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [Handling Multiple Sites on a Single Subscription](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/handling-multiple-sites-on-a-single-subscription/)
*   [Relink A Site To A WooCommerce Order And Subscription](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/relink-a-site-to-a-woocommerce-order-and-subscription/)
*   [Use A Customer's SSH Key For Servers](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/use-a-customers-ssh-key-for-servers/)
*   [Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce](https://web.archive.org/web/20240304144054/https://wpclouddeploy.com/documentation/woocommerce/technical-notes-for-how-we-implement-templating-sites-when-selling-wp-sites-with-woocommerce/)
