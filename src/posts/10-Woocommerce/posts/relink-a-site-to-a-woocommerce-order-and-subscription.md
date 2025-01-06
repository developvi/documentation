---
title: "Relink A Site To A WooCommerce Order And Subscription"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Relink A Site To A WooCommerce Order And Subscription
  parent: 10-Woocommerce
  order: 5
---
There are times you might need to link a new or existing site to a WooCommerce Order and Subscription. Some reasons you might need to do this are:

*   Accidental site deletion
*   Granting a customer access to a site that must be deleted when the subscription is cancelled.
*   Giving a customer an additional site that you’ve created for them and need to link to a subscription.

Here are the steps to get this done:

## 1\. Expose Hidden Site or Server Record Fields

*   Go to the DevelopVIDeploy → SETTINGS → MISC tab
*   Scroll down to the section titled **SHOW ADVANCED METABOXES**
*   Check the box
*   Scroll to the bottom of the screen and click the **SAVE SETTINGS** button

## 2\. Link or Relink Site Records To WooCommerce

*   Create a new site or navigate to an existing site record.
*   Scroll down to the **WORDPRESS APP** metabox – this is one of the hidden set of fields that were exposed when you turned on the option to SHOW ADVANCED METABOXES.
*   Change the **WOOCOMMERCE ORDER ID** field
*   Change the **WOOCOMMERCE SUBSCRIPTION ID** field
*   Click the **UPDATE** button in the upper right.

## Notes

*   DO NOT CHANGE ANY OTHER FIELDS!
*   You can only perform these steps if you are an ADMIN.
*   Turn off the SHOW ADVANCED METABOXES option when you are finished.

Here is what the advanced metabox will look like inside your site screen:

[![](https://web.archive.org/web/20240304155913im_/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-v4-258-1.png)](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-v4-258-1.png)

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy WordPress Sites](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/)
*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [WooCommerce Order Processing Notes](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-order-processing-notes/)
*   [Handling Multiple Sites on a Single Subscription](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/handling-multiple-sites-on-a-single-subscription/)
*   [Use A Customer's SSH Key For Servers](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/use-a-customers-ssh-key-for-servers/)
*   [Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce](https://web.archive.org/web/20240304155913/https://wpclouddeploy.com/documentation/woocommerce/technical-notes-for-how-we-implement-templating-sites-when-selling-wp-sites-with-woocommerce/)
