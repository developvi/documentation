---
title: "Use A Customer’s SSH Key For Servers"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Use A Customer’s SSH Key For Servers
  parent: 10-Woocommerce
  order: 6
---
There are two scenarios where you might want a customer to use their own ssh keys to login to a server:

1.  You want to grant them SSH access to a server
2.  You want to use their own keys in DVI so that all management functions in DVI is done with their keys

## 1\. Grant Customer SSH Access To A Server

For this situation you can simply add the customer’s public key to the root user’s ssh _authorized\_keys_ file. This file is usually located in the _~/.ssh_ folder. Just open it up with your favorite editor (NANO is easiest) and paste in the customer’s public SSH key.

nano ~/.ssh/authorized\_keys

*   Open up your existing public key on your local machine in any editor and copy it to the clipboard.
*   Paste it into the nano editor (usually using the right-mouse-click button). Make sure it’s on a new line – each public key needs to be on its own line.
*   Use ctrl-o to save the file.

Notice that in this case the customer does not have to reveal their private key to you.

## 2\. Use Customer’s SSH Keys For All DVI Functions

For this situation you have to swap out your keys in the DVI records for the customer keys. But first, you need to make sure that the customer’s PUBLIC key is added to the root user’s ssh _authorized\_keys_ file (see option 1 above).

Then, you need to update the server records to override the default global keys defined in SETTINGS :

*   Go to WpCloudDeploy → CLOUD SERVERS
*   Locate the customer’s server, hover over the title and click on the EDIT link
*   Click on the KEYS tab
*   Paste in the customer’s PRIVATE KEY and PUBLIC key into the corresponding fields
*   Click the SAVE button at the bottom.

To test the keys, you can use the SSH CONSOLE tab to run the **_ls_** command. If you get a popup with a list of files you’ll know all is good.

For this situation the customer will need to reveal their private key to you or you will need to [generate a keypair](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/) for them.

For more information about the KEYS tab see our documentation for [SSH KEY OVERRIDES](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/).

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy WordPress Sites](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/)
*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [WooCommerce Order Processing Notes](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-order-processing-notes/)
*   [Handling Multiple Sites on a Single Subscription](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/handling-multiple-sites-on-a-single-subscription/)
*   [Relink A Site To A WooCommerce Order And Subscription](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/relink-a-site-to-a-woocommerce-order-and-subscription/)
*   [Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce](https://web.archive.org/web/20240304141258/https://wpclouddeploy.com/documentation/woocommerce/technical-notes-for-how-we-implement-templating-sites-when-selling-wp-sites-with-woocommerce/)
