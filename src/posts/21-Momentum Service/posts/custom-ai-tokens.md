---
title: "Custom AI Tokens"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Custom AI Tokens
  parent: 21-Momentum Service
  order: 8
---
While there is a [standard list of AI tokens](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/ai-tokens/) available for use with all Momentum sites, you can create your own tokens.

Each custom AI token that you create can then be use anywhere on your template site.

As with a standard AI token, each custom token is associated with an AI PROMPT that is sent to OPENAI.

This makes **DevelopVIDeploy Momentum** extremely flexible and allows you to easily integrate your template site with generative AI text without writing custom code.

- - -

## Create A Custom AI Token

Navigate to **AI PROMPTS** → **ADD NEW AI PROMPT**. You will be shown the following screen:

[![](https://web.archive.org/web/20240420002140im_/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-01.png)](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-01.png)

*   **Title:** This can be anything you like – it’s only used to identify the token in the token list.
*   **Item Code**: This can be any string and is used to uniquely identify each prompt item.
*   **Replacement Code:** This is the token itself. Example: {{ai\_about\_us}}. Note that this field starts and ends with two curly brackets!
*   **Item Description:** A description of what the item does and/or where it will be used on the site etc.
*   **Prompt:** This is the prompt that will be sent to OPENAI to get generated text. You can find examples of prompts on the [standard AI tokens page](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/ai-tokens/). Notice that you can use data submitted from the onboarding form as part of the prompt.
*   **Item Type**: This should be left at the default of ‘standard’
*   **Template Type**: A user defined string that helps you group the tokens – this is optional
*   **Template Group**: Another optional user defined string that helps you group the tokens
*   **Do Not Delete On Submit:** Leave this checked. It tells the tenant plugin code that this item should not be removed when we’re cleaning up the template site to prepare it for a customer.
*   **Item Complete:** Leave this unchecked.

Leave all other fields blank and then click the **PUBLISH** button in the upper right of the screen.

- - -

## Using A Custom AI Token

After a custom AI token is created, you can use it anywhere on a template site. Here is an example of a custom token:

[![](https://web.archive.org/web/20240420002140im_/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-02.png)](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-02.png)

And here is that token used on a template site:

[![](https://web.archive.org/web/20240420002140im_/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-03.png)](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-tokens-03.png)

- - -

## Notes

Here are a couple of ideas on how you can use the **TEMPLATE TYPE** and **TEMPLATE GROUP** fields:

### Template Type

Use this when the site template might be used for different audiences – eg: if the template might support multiple industries and each group of AI prompts support different pages for each template. Otherwise, ok to leave blank.

If used for this purpose, it must match the **Template Type** field on the DVI template site record.

### Template Group

Use this when the template might be used for different audiences – eg: if the template might support multiple industries and each group of AI prompts support different pages for each template. Otherwise, ok to leave blank.

If used for this purpose, it must match the **Template Group** field on the DVI template site record.

- - -

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [How To Setup Products](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/how-to-setup-products/)
*   [About The Todo List](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/about-the-todo-list/)
*   [Replacement Tokens](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Custom AI Images](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/custom-ai-images/)
*   [Settings](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [WP-CONFIG.PHP Entries](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/wp-config-php-entries/)
*   [Customizing The Onboarding Form](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/customizing-the-onboarding-form/)
*   [Default Form Questions](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240420002140/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
