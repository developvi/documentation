---
title: "Customizing The Onboarding Form"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Customizing The Onboarding Form
  parent: 21-Momentum Service
  order: 12
---
The onboarding questionnaire (aka wizard or form) is built in Gravity Forms. You can add fields to the form at any time. But these fields will not be processed without modifying the **Momentum Tenant Plugin** to pick up the new field and values.

You can remove fields from the form either by deleting them (not recommended) or hiding them (recommended).

_Warning: Do not REMOVE and RE-ADD the same fields to the form – this changes the Gravity Forms FIELD ID which the **Momentum Tenant Plugin** code uses to extract the form data from each field. Unfortunately, Gravity Forms does not allow for the use of persistent field identifiers so we have to use the numeric id they provide. This id changes when you remove a field and re-add it._

If fields are removed and re-added, please remember to change the PHP code in the **Momentum Tenant Plugin** to use the new field id. For example, you might want to change the field type used – the only way to do that is to remove the field and re-add it, then change the PHP code to reference the new field ID.

Note that Gravity Forms is installed on the DevelopVIDeploy Primary Site and not on the tenant or template site. So when you’re looking to make modifications you need to search for it on the DVI Primary Site, not the tenant site.

When the customer completes the form, the data is posted to the tenant site where it’s processed by the **Momentum Tenant Plugin.**

If you add new fields to the form and want the **Momentum Tenant Plugin** to pick them up and create tokens, you can modify the _get\_gf\_fields\_ids\_array_() function directly (not recommended) or use the _dvi\_momentum\_get\_gf\_fields\_ids\_array_ filter in a custom plugin of your own to add the new fields to the array.

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [How To Setup Products](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/how-to-setup-products/)
*   [About The Todo List](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/about-the-todo-list/)
*   [Replacement Tokens](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [Custom AI Tokens](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/custom-ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Custom AI Images](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/custom-ai-images/)
*   [Settings](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [WP-CONFIG.PHP Entries](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/wp-config-php-entries/)
*   [Default Form Questions](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240420002723/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
