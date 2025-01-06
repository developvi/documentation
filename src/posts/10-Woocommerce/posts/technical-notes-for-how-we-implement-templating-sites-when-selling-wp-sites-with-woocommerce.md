---
title: "Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce
  parent: 10-Woocommerce
  order: 7
---
# Technical Notes For How We Implement Templating Sites When Selling WP Sites With WooCommerce

## Introduction

When a customer purchases a WP site in WooCommerce that is configured to be sourced from a site template, a series of complex processes kick off in the background. In this help article we aim to provide some color on how we’re handling this within the confines of DVI’s WordPress technology.

Truth be told, this article is to remind ourselves about what we did! To be blunt, things can get quite hairy! So, lets dive right in.

## High Level Walk-through

Template sites reside on a different server. So, when a purchase is made two things have to happen:

1.  The template site has to be copied from its server to the server where the new WP site will be located and
2.  The domain has to be changed to a new temporary domain.

This requires two back-to-back long running transactions that is sequenced properly.

For the first step, we use the function in our “Copy To New Server” tab, referred to internally as “site-sync”.

For the second step we use the function in our “Change Domain” tab.

## Challenges & Solutions

One of the biggest challenges in DVI (and also one of the benefits) is that a lot of activity occurs on action and filter hooks – some might say we overdo it on our ‘do\_action’ calls. They are very very convenient for triggering things and then moving on. But sometimes these hooks can’t quite get the data they need if they are two steps removed from where the data originated. For this feature where we need to run multiple long-running transactions, we absolutely required that the data be able to be passed between multiple independent action hooks in a particular sequence.

The only real way to do that was to use the database to pass the data.

So, in order to handle the sequencing we added the PENDING TASKS table/CPT.

Another thing we had to do was convert the ‘site sync’ and ‘change domain’ functions in the core plugin so that they could be triggered by action hooks instead of just being used directly in the UI via AJAX.

### Sequencing

Now, the sequencing depends on a few things:

1.  At the end of a long running transaction, a HOOK is fired for both the template site copy (“site sync”) and the domain change.
2.  The initial transaction in WooCommerce that triggered the hook must create and passed an array to the FIRST hook with all the data it needs for the rest of the process (including all intermediate hooks).

Thus, when the first long running transaction finishes (copying the template site – aka site-sync), its “I am done” action hook fires. That hook collects data from the PENDING TASKS using the COMMAND NAME as the key into the log. It does its thing but before it ends it updates the PENDING TASKS task as completed. It then fires off the second task (changing the domain of the newly copied site) by using a _do\_action_ call. That second task then does its thing, adds data to the PENDING TASKS table and, when it ends fires up its “I am done” action hook. That hook in turn picks up the data from the PENDING LOGS table, does its thing and marks the task complete.

## The Full Sequence

1.  When the order is placed, the function wp\_spinup\_wpapp is executed – triggered by WooCommerces’ _woocommerce\_payment\_complete_ hook.
2.  An array with all necessary data is created and the _wpcd\_wordpress-app\_do\_site\_sync_ hook is called via _do\_action_, passing that array as the second ‘args’ parameter.
3.  Just before _site sync_ is completed (which copies the template site to the server where the newly purchase site will reside), it adds a record to the PENDING TASKS table using the _command name_ as the key for the record.
4.  The after-action command hook (‘command\_completed’) for site-sync then fires, does some updates to the new site record and fires off another action hook to indicate that it is done. At this point there is no change to the PENDING TASKS table from step 3.
5.  The _wpcd\_wordpress-app\_site\_sync\_new\_post\_completed_ hook is fired. The function that handles this hook is named _site\_sync\_complete_. It does its thing and then marks the PENDING TASKS task complete. It then fires off a do\_action hook to trigger the domain change on the newly copied site. The hook being fired is _wpcd\_wordpress-app\_do\_change\_domain\_full\_live_.
6.  Just before the domain change is completed, it adds a record to the PENDING TASKS table using the _command name_ as the key for the record.
7.  Once again, the after-action command hook (“command\_completed”) fires. It does some updates to the new site record and fires off another action hook to indicate that it is done. At this point there is no change to the PENDING TASKS table from step 6.
8.  The _wpcd\_wordpress-app\_site\_change\_domain\_completed_ hook is fired. The function that handles this hook is named _site\_change\_domain\_complete_. This is where the final steps are done for the process – the new record is updated with all the user, order and similar info and emails sent to the end user. The PENDING TASKS record is updated as completed.

### More Topics In WooCommerce

*   [WooCommerce & DevelopVIDeploy WordPress Sites](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy-wordpress-sites/)
*   [WooCommerce & DevelopVIDeploy Servers](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-wpclouddeploy/)
*   [WooCommerce Order Processing Notes](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/woocommerce-order-processing-notes/)
*   [Handling Multiple Sites on a Single Subscription](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/handling-multiple-sites-on-a-single-subscription/)
*   [Relink A Site To A WooCommerce Order And Subscription](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/relink-a-site-to-a-woocommerce-order-and-subscription/)
*   [Use A Customer's SSH Key For Servers](https://web.archive.org/web/20240304141715/https://wpclouddeploy.com/documentation/woocommerce/use-a-customers-ssh-key-for-servers/)
