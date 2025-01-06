---
title: "Custom AI Images"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Custom AI Images
  parent: 21-Momentum Service
  order: 10
---
You can create Custom AI Image Prompts to generate images for each new customer site. These prompts will then be used to replace one or more images in your template site so that each customer site ends up with unique images.

- - -

## Create A Custom AI Image Prompt

Navigate to **AI IMAGE PROMPTS** → **ADD NEW AI IMAGE PROMPT**. You will be shown the following screen:

[![](https://web.archive.org/web/20240420001544im_/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-image-tokens-01.png)](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-momentum-custom-ai-image-tokens-01.png)

*   **Title:** This can be anything you like – it’s only used to identify the token in the token list.
*   **Item Code**: This can be any string and is used to uniquely identify each prompt item.
*   **Image URL:** This is the full url to the image that will be replaced starting with ‘http’ or ‘https’. The image url is for the image located on your template site. **DevelopVIDeploy Momentum** will automatically generate a URL appropriate for the customer site.
*   **Item Description:** A description of what the item does and/or where it will be used on the site etc.
*   **Prompt:** This is the prompt that will be sent to OPENAI to get the generated image.
*   **Template Type**: A user defined string that helps you group the tokens – this is optional
*   **Template Group**: Another optional user defined string that helps you group the tokens
*   **Do Not Delete On Submit:** Leave this checked. It tells the tenant plugin code that this item should not be removed when we’re cleaning up the template site to prepare it for a customer.
*   **Item Complete:** Leave this unchecked.

Leave all other fields blank and then click the **PUBLISH** button in the upper right of the screen.

- - -

## Using A Custom AI Image Prompt

You do not have to do anything special to use your prompt. **DevelopVIDeploy Momentum** will replace the image specified in the IMAGE URL field with a new AI Generated image.

- - -

## Important Notes

AI Generated Images are **extremely sensitive** to your prompts. If you do not construct your prompts properly you will get poor and nonsensical images. If you are new to AI Prompts you can use a site like [PROMPT HERO](https://web.archive.org/web/20240420001544/https://prompthero.com/) to search for prompt ideas.

Some page builders and Gutenberg blocks do not place the image URL in the database. In these instances, the images cannot be replaced by our AI generated ones. For example, the background image in a column block for the STACKABLE blocks seem to result in the URL to the image being placed in a stylesheet.

Other page builders such as ELEMENTOR format their URLS in a non-standard way. This means when we search for those URLs we will not find them – so those cannot be replaced with AI generated images.

- - -

## Other Notes

Here are a couple of ideas on how you can use the **TEMPLATE TYPE** and **TEMPLATE GROUP** fields:

### Template Type

Use this when the site template might be used for different audiences – eg: if the template might support multiple industries and each group of AI prompts support different pages for each template. Otherwise, ok to leave blank.

If used for this purpose, it must match the **Template Type** field on the DVI template site record.

### Template Group

Use this when the template might be used for different audiences – eg: if the template might support multiple industries and each group of AI prompts support different pages for each template. Otherwise, ok to leave blank.

If used for this purpose, it must match the **Template Group** field on the DVI template site record.

- - -

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [How To Setup Products](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/how-to-setup-products/)
*   [About The Todo List](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/about-the-todo-list/)
*   [Replacement Tokens](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [Custom AI Tokens](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/custom-ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Settings](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [WP-CONFIG.PHP Entries](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/wp-config-php-entries/)
*   [Customizing The Onboarding Form](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/customizing-the-onboarding-form/)
*   [Default Form Questions](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240420001544/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
