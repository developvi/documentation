---
title: "Translations"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Translations
  parent: 07-Others-&-Misc
  order: 3
---
One of the biggest benefits of DVI over an SaaS product is the ability to use your WordPress Management Dashboard in your language. And by extension you have the ability to offer your customers a user-experience in their native language as well.

Translating DVI uses the same process that all other WordPress plugins uses. You can learn more about this process in the [WordPress developer handbook](https://web.archive.org/web/20240529150606/https://developer.wordpress.org/plugins/internationalization/localization/).

## Translating Strings

1.  Using your favorite translation tool, update the POT file. We already provide POT files in each of our plugins and add-ons in the _languages_ folder. So you just need to load that up and let the tool update it – in most cases there aren’t any changes to be made but it’s a good first step to ensure that you’re working with the latest strings. Most users use [POEDIT](https://web.archive.org/web/20240529150606/https://poedit.net/) to do this. (Note that POEDIT is good for storing and managing the file on your local file system. But, using it on a remote WordPress site will not guarantee that the final language files end up in their correct folders – see relocating files in the next section.)
2.  Copy the POT file to a file with the same name but with a PO extension AND with the locale name inserted in the correct location as dictated by the WP translation standards. For example, the _wpcd.pot_ file should be copied to _wpcd-de\_DE.po_ for German. Note that some locales can be longer than 5 chars (eg: de\_DE\_formal).
3.  Open the PO file and apply your translations.
4.  Using your translation tool, create the MO file from your PO file. The MO file is a compiled version of your PO file – this is what WordPress loads up and uses for translations at runtime.

## Relocating Translation Files For DevelopVIDeploy CORE

Now that you have your MO file, it’s time to make sure that it ends up in the CORRECT folder on your WordPress installation.

Your **wpcd-{locale}.mo** file should be placed in either the _wp-content/languages/_ **OR** _wp-content/languages/plugins/wpcd_ folder. We search both locations for the MO file.

## Relocating Translation Files For DevelopVIDeploy Add-ons

DVI Add-on translation files need to be placed in a separate folder under _wp-content/languages/plugins_. The name of this folder is very important.

The folder should be the same name as the primary add-on file. For example, for a REDIS translation, the folder should be _wp-content/languages/plugins/wpcd-redis_. Then, the MO file is placed under this folder and should have the name **wpcd-redis-{locale}.mo**. For example, a German translation will be _wp-content/languages/plugins/wpcd-redis/wpcd-redis-de\_DE.mo._

## Existing Translations

All of our translations are provided by customers and volunteers. You can find those translations in our [POEDITOR Translation Project](https://web.archive.org/web/20240529150606/https://poeditor.com/join/project?hash=A5I1lpqRes). Navigate there and you’ll be able to download any existing translations.

## Tips & Resources

*   If you’re not sure what your locale is, you can [look it up on translate.wordpress.org](https://web.archive.org/web/20240529150606/https://translate.wordpress.org/).
*   You can also place the MO file in the _languages_ folder in each plugin/add-on. However, this will be overwritten every time the plugin/add-on is updated. So it’s best to move it into the _wp-content/languages_ folder.

- - -

## Contributing

If you’d like to contribute to translations, you can do so in our POEDITOR project located here: [DVI POEDITOR project](https://web.archive.org/web/20240529150606/https://poeditor.com/join/project?hash=A5I1lpqRes)

- - -

## Notes

*   At least one customer reported that they needed to **re-save permalinks** after updating translations with POEDIT or WPML for checkout to work properly with our WooCommerce add-ons. It might be related to their site configuration or customizations made or it could be something about how WP translations work that we don’t quite understand yet.

- - -

### More Topics In Other & Misc

*   [Using Our DigitalOcean Template Image](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/digitalocean-template-image/)
*   [Using Our AWS EC2 Core Template](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-template-image/)
*   [AWS EC2 Premium Template](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-premium-template-image/)
*   [Moving The DVI Plugin To A New Server](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/moving-the-wpcd-plugin-to-a-new-server/)
*   [Simultaneous Dashboard Actions](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/simultaneous-dashboard-actions/)
*   [White Label](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/white-labelling/)
*   [Command, SSH & Error Logs](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/command-ssh-error-logs/)
*   [Server Groups](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/server-groups/)
*   [Application (Site) Groups](https://web.archive.org/web/20240529150606/https://wpclouddeploy.com/documentation/other-misc/application-site-groups/)
