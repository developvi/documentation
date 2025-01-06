---
title: "WP-CONFIG.PHP Entries"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WP-CONFIG.PHP Entries
  parent: 21-Momentum Service
  order: 12
---

The following entries are required in the wp-config.php file for your template site. We will, of course, have added these for you as part of the **DevelopVIDeploy Momentum** service. But, you might need to change these in the future (eg: when an api key is compromised) so you need to aware that these exists.

Plus, as you create additional templates, you might want these to have different parameters.

define( 'OPENAI\_API\_KEY', 'your\_openapi\_key' );

If you are using FLUENTSMTP or the MAILGUN plugin, you’ll find additional entries related to these items as well.

- - -

In the todo list for each tenant site there’s a link to the WooCommerce account area. The URL for that link is in the tenant wp-config.php file.

define( 'WPMT\_WC\_MY\_ACCOUNT\_LINK', 'https://yourdomain.com/my-account' ) ;

Note that the URL must start with https://.

For more information about this entry please see the [MISC page](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/misc/).

- - -

If you’re using a page builder / theme in the tenant site other than KADENCE, you should set the name in wp-config.php

define( 'WPCD\_MOMENTUM\_TENANT\_PAGEBUILDER', 'none' ) ;

or something like

define( 'WPCD\_MOMENTUM\_TENANT\_PAGEBUILDER', 'blocksy' ) ;

You can then use this value in the tenant custom plugin to conditionally do things that do not apply to other page builders and themes such as Kadence.

- - -

### More Topics In Momentum

*   [About wpclouddeploy Momentum](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/about-wpclouddeploy-momentum/)
*   [No-Charge Customizations](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/no-charge-customizations/)
*   [The Workflow In Pictures](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/the-workflow-in-pictures/)
*   [Template Sites](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/template-sites/)
*   [How To Setup Products](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/how-to-setup-products/)
*   [About The Todo List](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/about-the-todo-list/)
*   [Replacement Tokens](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/tokens/)
*   [AI Tokens](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/ai-tokens/)
*   [Custom AI Tokens](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/custom-ai-tokens/)
*   [AI Featured Images](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/ai-featured-images/)
*   [Custom AI Images](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/custom-ai-images/)
*   [Settings](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/settings/)
*   [Customizing The Onboarding Form](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/customizing-the-onboarding-form/)
*   [Default Form Questions](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/default-form-questions/)
*   [Theme & Page Builder Compatibility](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/theme-page-builder-compatibility/)
*   [Default Color Palettes](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/default-color-palettes/)
*   [Misc](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/misc/)
*   [Automatic Updates & Support](https://web.archive.org/web/20240420010603/https://wpclouddeploy.com/documentation/momentum/automatic-updates-support/)
