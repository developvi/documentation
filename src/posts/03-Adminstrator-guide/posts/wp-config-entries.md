---
title: "WP-CONFIG Entries"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WP-CONFIG Entries
  parent: 03-Adminstrator-guide
  order: 14
---
DevelopVIDeploy has a few options that can be added to your WordPress wp-config.php file to activate, remove or modify certain functions.

- - -

## Security Options

- - -

#### WPCD\_ENCRYPTION\_KEY

define( WPCD\_ENCRYPTION\_KEY', 'your very long encryption key goes here' );

Certain passwords and other pieces of sensitive data are encrypted when stored in the database. This defines the encryption key that is used. **We strongly urge that you add this entry to your wp-config.php file**.

Prior to version 4.1.0, we would use a hardcoded default key if you did not provide one. Frankly, this was the same as no key because everyone could view it by looking at the source code of the plugin.

As of version 4.1.0 (and later of course), we generate a key and store it in the database for you. BUT, this is still not as secure as could be since the key is stored in plaintext, you do not know what it is and even a mild compromise of the database can expose the key. Further, since you do not know the temporary key we’re storing in the database, you cannot use the backup & restore settings option to move to a new installation (since the encrypted credentials cannot be decrypted in the new installation.)

**So, you really need to create a wp-config.php entry** – preferably before you start configuring your cloud providers. _If you create this entry after you configure your cloud providers you will need to re-enter your api keys and other credential information in settings._

Here are some ways you can generate a string for this key:

*   Use a password generation program such as LASTPASS or KEEPASS
*   Use any tool that generates WordPress SALTS
*   Create a new SSH KEYPAIR and use a portion (or all) of the private key (this idea was provided by one of our customers.)

- - -

## General WP-CONFIG Options

- - -

#### DISABLE\_WPCD\_CRON

define('DISABLE\_WPCD\_CRON', true);

Prevent the WordPress Cron process from running DVI Cron jobs. This is used in conjunction with our “Better DVI Cron” setup.

[More About Better DVI Crons](https://web.archive.org/web/20240420014544/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)

- - -

#### WPCD\_HIDE\_SSH\_CONSOLE

define('WPCD\_HIDE\_SSH\_CONSOLE', true);

Hide the SSH CONSOLE from the server detail screen.

- - -

#### WPCD\_DEBUG

define('WPCD\_DEBUG', false);

Turn on some debugging options that will write additional debugging data to the WordPress debug.log file.

- - -

#### WPCD\_LOAD\_BACKUP\_DO\_PROVIDER

define('WPCD\_LOAD\_BACKUP\_DO\_PROVIDER', true);

We provide two digital ocean providers so that you can use two different accounts if you like. But by default we don’t load the second one. Turn on the second one (‘backup’) using this wp-config entry.

If you have a license for our [VIRTUAL PROVIDER](https://web.archive.org/web/20240420014544/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/) add-on, you do not need to use this option (since the Virtual Provider add-on allows you to use as many provider accounts as you like.)

- - -

#### WPCD\_SKIP\_SERVER\_SIZES\_SETTING

define('WPCD\_SKIP\_SERVER\_SIZES\_SETTING', true);

The server sizes that are shown in the settings screen under each provider is currently only used by the VPN and BASIC SERVER apps and the WORDPRESS app WOOCOMMERCE add-ons. This option allows those sizes to be hidden which can be useful if the none of these apps or add-ons are enabled.

- - -

#### WPCD\_SHOW\_PERMISSION\_LIST

define('WPCD\_SHOW\_PERMISSION\_LIST', true);

The permission list is an internal post type that we use for setting up permissions for teams. In most cases it’s not necessary to show this list on the screen.

- - -

#### WPCD\_DISABLE\_DATA\_SYNC

define('WPCD\_DISABLE\_DATA\_SYNC', true);

Data syncing allows server and site metadata to be pushed to a destination DVI site as a form of semi-real-time backup. Use this flag to disable the option entirely.

- - -

#### WPCD\_ALLOW\_DUPLICATE\_DOMAINS

define('WPCD\_ALLOW\_DUPLICATE\_DOMAINS', true);

Under normal circumstances you do not want duplicate domains in your system. But, when testing you might need this ability as you test creating sites on multiple servers and so on. Use this flag to enable duplicate domains. Keep in mind that this will break some functions where we can’t identify the correct records to update based on just the domain name.

- - -

#### WPCD\_DISABLE\_EMAIL\_NOTIFICATIONS

define('WPCD\_DISABLE\_EMAIL\_NOTIFICATIONS', true);

Disables the options and metaboxes on the SERVERS and SITES screen that allow for emailing to owners and other interested parties associated with those items. If this feature is not being used, it’s a good way to declutter the screen.

- - -

#### WPCD\_HIDE\_CHANGELOG\_IN\_PLUGIN\_LIST

define('WPCD\_HIDE\_CHANGELOG\_IN\_PLUGIN\_LIST', true);

Prevents the change log from showing in the WordPress plugins list screen. See [_https://developvideploy.com/whats-new-in-developvideploy-4-16/_](https://web.archive.org/web/20240420014544/https://developvideploy.com/whats-new-in-developvideploy-4-16/) for more information.

- - -

## Multisite / SAAS Related Entries

- - -

#### WPCD\_SKIP\_WELCOME\_MESSAGE

define( 'WPCD\_SKIP\_WELCOME\_MESSAGE' , false);

When enabled, will not add the DVI welcome message to the top of the settings screen on the general tab. However, app specific welcome messages will still be shown. A better way to handle replacing the welcome message might be to use the _wpcd\_settings\_welcome\_text\_initial_ filter which allows you to completely replace the text or append to it.

- - -

#### WPCD\_SKIP\_SSH\_TIMEOUT\_SETTINGS

define( 'WPCD\_SKIP\_SSH\_TIMEOUT\_SETTINGS',  false );

When enabled, you will not see the SSH timeout options on the settings screen.

- - -

#### WPCD\_AUTO\_TRIM\_LOG\_LIMIT

define( 'WPCD\_AUTO\_TRIM\_LOG\_LIMIT' , 100);

Overrides the auto trim log limit set in the settings screen (under the logs tab).

- - -

#### WPCD\_MENU\_NAME

define( 'WPCD\_MENU\_NAME' , 'Servers and Sites');

Overrides the name for the main menu item.

- - -

#### WPCD\_APP\_MENU\_NAME

define( 'WPCD\_APP\_MENU\_NAME' , 'All Sites');

Overrides the name for the applications menu item.

- - -

#### WPCD\_SHORT\_NAME

define( 'WPCD\_SHORT\_NAME' , 'FireupWP');

The product name to show on certain screens, eg: Wizard.

- - -

#### WPCD\_LONG\_NAME

define( 'WPCD\_LONG\_NAME' , 'FireupWP - Easiest Way To Fireup A New WP Server');

The product description to show on certain screens (not currently used anywhere).

- - -

#### WPCD\_WPAPP\_MENU\_NAME

define( 'WPCD\_WPAPP\_MENU\_NAME' , 'WP Sites');

Overrides the name for the WordPress sites menu item.

_Available in DVI V 4.2.5 or later._

- - -

#### WPCD\_HIDE\_HELP\_TAB

define( 'WPCD\_HIDE\_HELP\_TAB' , true);

In versions prior to 4.2.5, this option hides the help tab in the settings screen. In version 4.2.5 and later, the help area moved to the main menu but this option still allows you to hide it.

- - -

#### WPCD\_HIDE\_PROVIDER\_HELP\_LINKS

define( 'WPCD\_HIDE\_PROVIDER\_HELP\_LINKS' , true);

Hides the help links in the provider screen that point back to the DVI help pages.

- - -

#### WPCD\_SITE\_PACKAGES\_NO\_BASH

define(  'WPCD\_SITE\_PACKAGES\_NO\_BASH', true);

Does not show options for bash scripts in site packages nor allow execution of those scripts even if values are present.

This is useful when DVI is installed in a shared SaaS environment – one where there are multiple instances of DVI on the same server with different customers allowed to access each instance. In this case you might not want customers executing bash scripts that they define.

If a shared environment as described in the prior paragraph is your use-case then this needs to be added to your wp-config.php file in your TEMPLATE sites so that all your customer sites inherits it. If, for some reason, your existing customer sites do not have it, then it should be added.

This option is available in DVI 5.4.1 and later.

- - -

#### WPCD\_CUSTOM\_SCRIPTS\_NO\_BASH

define(  'WPCD\_CUSTOM\_SCRIPTS\_NO\_BASH', true);

Do not allow execution of bash scripts specified in then **DevelopVIDeploy → SETTINGS → APP: WORDPRESS SETTINGS → CUSTOM SCRIPTS** tab.

This is useful when DVI is installed in a shared SaaS environment – one where there are multiple instances of DVI on the same server with different customers allowed to access each instance. In this case you might not want customers executing bash scripts that they define.

If a shared environment as described in the prior paragraph is your use-case then this needs to be added to your wp-config.php file in your TEMPLATE sites so that all your customer sites inherits it. If, for some reason, your existing customer sites do not have it, then it should be added.

This option is available in DVI 5.4.1 and later.

- - -

## APP Specific Entries: WPAPP

- - -

#### WPCD\_WPAPP\_SKIP\_POPUP\_HEADER

define('WPCD\_WPAPP\_SKIP\_POPUP\_HEADER', true);

This entry applies specifically to the WordPress app. When provisioning a server or app the popup has a large header with the “WPCloud Deploy” name on it. Set this entry to avoid showing that.

- - -

#### WPCD\_WPAPP\_HIDE\_INSTALLWP\_HOVER\_LINK

define('WPCD\_WPAPP\_HIDE\_INSTALLWP\_HOVER\_LINK', true);

This entry applies specifically to the WordPress app. The servers list will usually show an INSTALL WORDPRESS link under the title column when the user/admin hovers over a title. However, there’s a lot of links there and sometimes you might just want to remove this particular link since you have a separate column with a specific button for installing WordPress. This wp-config option gives you the ability to do so – setting it to TRUE will remove the link.

- - -

#### WPCD\_WPAPP\_HIDE\_WEBSERVER\_OPTIONS

define('WPCD\_WPAPP\_HIDE\_WEBSERVER\_OPTIONS', true);

This entry applies specifically to the WordPress app. When we start to support multiple webservers, this will disable the drop-down that allows the user to select a webserver type when deploying a new server. This option is only available as of DVI V 5.0.

- - -

### Other Entries

Please make sure you review the other entries described earlier in this document if you’re running DVI in a shared environment – i.e.: one where there are multiple instances of DVI, each of which is assigned to a different customer.

- - -

## Testing & Development Options

- - -

#### WPCD\_LOAD\_VPN\_APP

define('WPCD\_LOAD\_VPN\_APP', true);

Activates the VPN module

The **VPN** Module provides the capability to sell a VPN server subscription via WooCommerce. It requires the WooCommerce, WooCommerce Subscriptions and WooCommerce Memberships plugins to work.

There is no further documentation available for this module and no technical support is available if you activate it.

- - -

#### WPCD\_LOAD\_BASIC\_SERVER\_APP

define('WPCD\_LOAD\_BASIC\_SERVER\_APP', true);

Activates a basic server app module.

The **Basic Server** Module provides the capability to sell a Basic Server subscription via WooCommerce. It requires the WooCommerce, WooCommerce Subscriptions and WooCommerce Memberships plugins to work.

There is no further documentation available for this module and no technical support is available if you activate it.

- - -

#### WPCD\_LOAD\_STABLEDIFF\_APP

define('WPCD\_LOAD\_STABLEDIFF\_APP', true);

Activates an app the creates a STABLE DIFFUSION AI server.

This Module provides the capability to sell a Stable Diffusion AI server subscription via WooCommerce. It requires the WooCommerce, WooCommerce Subscriptions and WooCommerce Memberships plugins to work.

There is no further documentation available for this module and no technical support is available if you activate it. If you’d like more information about this, please contact our sales or support team.

- - -

## Deprecated Options

- - -

#### WPCD\_SERVER\_HIDE\_TABS\_WHEN\_AUTHOR

define( 'WPCD\_SERVER\_HIDE\_TABS\_WHEN\_AUTHOR' , 'server-ssh-keys,server-users,ssh\_console,server\_upgrade,fail2ban');

Remove certain server tabs from the server screen even when the user is an Author with full rights to the server. This helps in SaaS situations where the post author is the buyer but you still don’t want them to access those tabs.

You specify the list of tabs to be disabled when the user is an author as a comma-delimited string with no spaces between each entry. There are currently only 5 tabs that can be disabled this way.

*   server-ssh-keys
*   server-users
*   ssh\_console
*   server\_upgrade
*   fail2ban

_As of DVI V 4.13.0, you no longer need to use this option since there is a UI in the settings screen that accomplishes the same thing. We will likely remove this option in a future version so consider this option deprecated._

#### WPCD\_WPAPP\_SHOW\_WEBSERVER\_OPTIONS

define('WPCD\_WPAPP\_SHOW\_WEBSERVER\_OPTIONS', true);

This entry applies specifically to the WordPress app. When we start to support multiple webservers, this will enable the drop-down when deploying a new server. Currently, if you turn this on, it will show a drop-down of web server choices but your choice will have no effect.

_This option has been removed in DVI V 5.0 and replaced with WPCD\_WPAPP\_HIDE\_WEBSERVER\_OPTIONS._

- - -

## Notes

- - -

When adding any of the options to your _wp-config.php_ file, please make sure that they are placed above the line that says _“/\* That’s all, stop editing! \*/”_ in wp-config.php. Do not add them to the bottom of the file!
