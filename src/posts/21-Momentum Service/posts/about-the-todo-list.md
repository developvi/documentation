---
title: "About The Todo List"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: About The Todo List
  parent: 21-Momentum Service
  order: 5
---
The Todo list or “checklist” is a custom list of items that you can present to the customer so that they know what needs to be done to get the site ready for production.

This is useful if you’re selling site subscriptions for a niche without white-glove service and it’s up to the customer to do the work to complete the site.

If you’re using **DevelopVIDeploy Momentum** for quick prototyping or to sell niche site subscriptions with white-glove service then it’s unlikely that you will be using this feature.

Here is the default TODO list that is included with the baseline Momentum setup:

[![](https://web.archive.org/web/20240420000125im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/Snag_306c1779.png)](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/wp-content/uploads/2023/12/Snag_306c1779.png)

You can add custom items to this list without writing custom code. But you cannot remove remove the default items (shown in the image above) without code modifications.

- - -

## How To Add A Custom Todo Item

You can add custom Todo items that do not need special handling or processing. To do this:

*   On your template site, navigate to the **ADMIN CHECKLIST** menu option. (Usually the list would be empty unless you’ve added items to it already or we’ve added some due to your customizations requests.)
*   At the top of the blank list click the **ADD NEW ITEM** button.
*   Enter a TITLE at the top of the screen – this will be shown in the ADMIN list of todo items as the first column
*   Enter an ITEM CODE – Must be unique for the entire list and consist only of alpha-numeric characters and underscores
*   Enter the SORT ORDER – this will indicate where in the TODO LIST the item will appear – if you do not enter this, the item will not show up in the list
*   Check the box for “SHOW IN CHECKLIST UI”.
*   Check the box for “DO NOT DELETE ON SUBMIT”.
*   All other fields are optional.

The **DO NOT DELETE ON SUBMIT** checkbox is what tells the tenant plugin code that this item should not be removed when we’re cleaning up the template to prepare it for a customer.

[![](https://web.archive.org/web/20240420000125im_/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-todo-list-03.png)](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/wp-content/uploads/2023/12/wpcd-momentum-todo-list-03.png)

- - -

## Automatically Redirecting To The Todo List

*   When a user logs in to a tenant site, they will be redirected to the checklist page IF they are not an admin AND if they have the ability to edit posts.
*   Admins should redirect to the wp-admin dashboard (assuming no other plugin overrides this function).
*   Standard users should remain on the front-end of the site (assuming no other plugin overrides this function).

- - -

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [How To Setup Products](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/how-to-setup-products/)
*   [Replacement Tokens](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [Custom AI Tokens](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/custom-ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Custom AI Images](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/custom-ai-images/)
*   [Settings](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [WP-CONFIG.PHP Entries](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/wp-config-php-entries/)
*   [Customizing The Onboarding Form](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/customizing-the-onboarding-form/)
*   [Default Form Questions](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240420000125/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
