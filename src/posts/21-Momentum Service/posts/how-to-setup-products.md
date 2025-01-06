---
title: "How To Setup Products"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Setup Products
  parent: 21-Momentum Service
  order: 4
---
Setting up products in **DevelopVIDeploy Momentum** is a bit more complex than you probably expect it would be. This is because we want to provide as much flexibility as possible:

1.  We want to bypass the WooCommerce storefront and go directly from the pricing page to the cart
2.  We want to have upgrade and downgrade options – this means using WooCommerce GROUPED Products. WooCommerce Grouped Products have complex URLs
3.  We want the flexibility to associate multiple templates with a single industry and vice-versa

In order to make this work we have to create a bridge between industries, templates, pricing pages and WooCommerce.

Still, you can break down setting up product into three components:

1.  Create individual products inside WooCommerce linked to our template sites
2.  Create a grouped product inside WooCommerce the combine the products created in step one
3.  Create product links and assign template images

The entire process is more tedious than it is hard. And a lot of it is copy-and-paste or using a DUPLICATE function.

Before you can do any of that though, you have to setup your industries. If you’ve requested that industries be removed from your workflow then you can skip this step.

- - -

## Setup Industries

*   Navigate to **DVI PRODUCTS** → **INDUSTRIES**
*   Give your industry a name and add at least one image with the industry name in it
*   Click the **ADD NEW INDUSTRY** button at the bottom of the page to save it.

Here is an example of how industries will be displayed as the user progresses through the checkout process – notice that it is a 3-column grid.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-01.png)

In this example we are using images that are the same as the template images. Most admins will likely just use solid or gradient images with the industry text on it and a small image or icon. Here is an example of a more minimalistic layout:

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-03.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-03.png)

- - -

## Setup Individual WooCommerce Products

Let’s assume you have a 3-tier pricing plan, imaginatively titled “Starter”, “Premiere” and “Professional”.

For each template you have, you will create THREE individual WooCommerce products – one for each pricing plan level.

If you are offering 6 templates across various industries, this means you’ll create 18 products (6 templates X 3 price levels).

To setup a single product in WooCommerce:

*   Navigate to the **PRODUCTS** → **ADD NEW** screen.
*   Enter the **PRODUCT NAME** – eg: _Interior Design Medium_.
*   Products must be of type **SIMPLE SUBSCRIPTION.**
*   The checkbox for **THIS IS A WORDPRESS SITE** located under the **WORDPRESS SITES** tab must be turned on.
*   Click on the _Inventory_ tab to enable stock management – turn on the option for _Sold Individually_.
*   In most cases you would want to check the **VIRTUAL** option as well since it’s not something that is being shipped.
*   In the **PUBLISH** metabox in the upper right, set the **CATALOG VISIBILITY** option to _HIDDEN_ – this prevents the customer from accidentally locating the individual product screen and using it for checkout.

Since we would have already setup at least one product for your installation, you can usually use the DUPLICATE option in the product list.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-01.png)

## Setup Grouped Products

Once you have created at least one product for each price level for your template(s), you now need to create a GROUPED product for each template.

The components of the grouped product will be the individual products you setup in the prior section

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-02-1.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-industries-wc-product-02-1.png)

- - -

## Setup DVI PRODUCT GROUPS

Before we can setup the BRIDGES that link industries, templates, pricing pages and WooCommerce, we need to setup DVI PRODUCT GROUPS. These groups will map to your pricing plan levels.

So, in the example above, you’ll setup three DVI PRODUCT GROUPS – “Starter”, “Premiere” and “Professional”.

To create a DVI PRODUCT GROUP, navigate to **DVI PRODUCTS** → **NEW PRODUCT GROUP**

Setup one group for each pricing plan.

- - -

## Setup Bridges

We mentioned at the beginning of this document that we need to create a bridge between industries, templates, pricing pages and WooCommerce. The mechanism for that bridge is the DVI PRODUCTS screen.

You will create one DVI PRODUCT for each template and pricing level combination.

In the example we’re using with three pricing levels and one template, you’ll create three DVI PRODUCT entries.

To create your first DVI PRODUCT bridge just navigate to **DVI PRODUCTS** → **ADD NEW PRODUCT**

The first field you have to fill in is the TITLE. You should use something that comprises of the Template type or type and the price level – eg: INTERIOR DESIGN – STARTER.

The next field is the PURCHASE LINK.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-purchase-link-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-purchase-link-01.png)

The purchase link is tricky – it consist of three parts:

*   The base url
*   The product ID of the grouped WooCommerce product
*   The product ID of the component product inside the grouped product.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-purchase-link-02.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-purchase-link-02.png)

In the image above:

1.  This is the base URL. You’ll notice that it composes of the URL to your primary DVI site followed by _/checkout/?add-to-cart=_
2.  This is the WooCommerce product id of the WooCommerce GROUPED product followed by “&”.
3.  This is the product id of the a component of the grouped product in the format _quantity\[id\]=1_

#### Assign DVI PRODUCT GROUPS

You should assign each DVI PRODUCT to a **single** DVI PRODUCT GROUP (which you created in the prior section above.) Since the purchase link will only add one WooCommerce product to the cart, selecting multiple DVI PRODUCT GROUPS will not work – this is because the WooCommerce product being added to the cart will only belong to a single plan. So each product bridge setup must only be associated with a single plan.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-product-groups-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-product-groups-01.png)

#### Assign Template Images

For each industry you’re supporting, you’ll need to add a template image. This is the image the customer will see when they go through the checkout process.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-product-industry-template-images-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-product-industry-template-images-01.png)

- - -

## Pricing Page

All of the product setup you’ve done so far is in support of creating a pricing page that bypasses the WooCommerce storefront.

Here is an example of a pricing page – the key is the URL in the button. This section will discuss how to construct that URL.

[![](https://web.archive.org/web/20240419235628im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-pricing-page-01.png)](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-pricing-page-01.png)

The three links in the three buttons above are:

*   \[baseurl\]/display-templates?wpcd\_display\_template\_action=industry&wpcd\_display\_template\_plan=starter
*   \[baseurl\]/display-templates?wpcd\_display\_template\_action=industry&wpcd\_display\_template\_plan=professional
*   \[baseurl\]/display-templates?wpcd\_display\_template\_action=industry&wpcd\_display\_template\_plan=premiere

The difference between the three links is the PLAN – you’ll notice at the end, each references a different plan. These plans are the SLUGS of the DVI PRODUCT GROUPS.

- - -

## How It All Fits Together

When the customer clicks on a button on the pricing page, the system knows what PLAN the user clicked on because the plan slug is in the URL.

When the customer selects their industry from the INDUSTRY Page (a sample shown earlier above), the plan slug is passed along to the next step (select template)

The plan slug is used to select DVI PRODUCTS and from those products, template images that match the industry are selected. These are the images that the customer is shown so that they can select a template. For the simplest setups, there will only be one template.

By doing things this way, you can place the pricing URLS anywhere – even on other sites and landing pages. And they will all bypass the WooCommerce store front while harnessing the flexibility of WooCommerce (coupons, upsells & downsells, flexible subscription periods, trials, payment gateways etc.)

- - -

## Notes

*   If this all seems complex to you, don’t worry too much about it. We’ll have set up a lot of this for you as part of the MOMENTUM service package. You’ll likely just do light editing for things such as product descriptions and pricing levels.
*   While it may not be immediately obvious, the tedious product setup process allows for a single template to support multiple industries and use-cases. For simple setups, there will be one template per industry but for experienced developers, a single template can be used to support multiple industries.

- - -

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [About The Todo List](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/about-the-todo-list/)
*   [Replacement Tokens](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [Custom AI Tokens](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/custom-ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Custom AI Images](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/custom-ai-images/)
*   [Settings](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [WP-CONFIG.PHP Entries](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/wp-config-php-entries/)
*   [Customizing The Onboarding Form](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/customizing-the-onboarding-form/)
*   [Default Form Questions](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240419235628/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
