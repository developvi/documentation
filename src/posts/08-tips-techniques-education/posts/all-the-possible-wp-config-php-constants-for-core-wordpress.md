---
title: "All The Possible WP-CONFIG.PHP Constants For Core WordPress"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: All The Possible WP-CONFIG.PHP Constants For Core WordPress
  parent: 08-tips-techniques-education
  order: 6
---
## PHP memory limits for the site

`define( 'WP_MEMORY_LIMIT', '128M' );`
`define( 'WP_MAX_MEMORY_LIMIT', '256M' ); // Increase admin-side memory limit.`

## Database

`define( 'WP_ALLOW_REPAIR', true ); // Allow WordPress to automatically repair your database.`
`define( 'DO_NOT_UPGRADE_GLOBAL_TABLES', true ); // Don't make database upgrades on global tables (like users)`

## Explicitly setting url

`define( 'WP_HOME', 'http://domain.com' );`
`define( 'WP_SITEURL', 'http://domain.com' );`

## Set url to… whatever…

`define( 'WP_HOME', 'http://' . $_SERVER['HTTP_HOST'] );`
`define( 'WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST'] );`

## Set default theme

`define( 'WP_DEFAULT_THEME', 'twentytwentyone' );`

## Prevent New Themes From Being Added When WP Updates

`define( 'CORE_UPGRADE_SKIP_NEW_BUNDLED', true );`

This one’s confusing because the the source code comments say it must be set to FALSE:

See source here: [https://core.trac.wordpress.org/browser/tags/5.3/src/wp-admin/includes/update-core.php#L810](https://web.archive.org/web/20240304154809/https://core.trac.wordpress.org/browser/tags/5.3/src/wp-admin/includes/update-core.php#L810)

## Temporary for causing a site to relocate. Remove after login

`define( 'RELOCATE', true );`

## Allow WordPress to update files

`define( 'FS_METHOD', 'direct' );`
`define( 'FS_CHMOD_DIR', ( 0755 & ~ umask() ) ); // change permissions of directories`
`define( 'FS_CHMOD_FILE', ( 0644 & ~ umask() ) ); // change permissions of files`

## Set the directory files should be downloaded to before they’re moved

This is usually set in the PHP conf
`define( 'WP_TEMP_DIR', '/Applications/MAMP/tmp/php/' ); // this one is for default MAMP setup`

## Content, plugin, and template paths

`define( 'WP_CONTENT_URL', get_option( 'siteurl' ) . '/wp-content' ); // Full URL to wp-content`
`define( 'WP_CONTENT_DIR', ABSPATH . 'wp-content' ); // No trailing slash, full paths only to wp-content`
`define( 'WP_PLUGIN_DIR', WP_CONTENT_DIR . '/plugins' ); // Full path, no trailing slash.`
`define( 'WP_PLUGIN_URL', WP_CONTENT_URL . '/plugins' ); // Full URL, no trailing slash.`
`define( 'PLUGINDIR', 'wp-content/plugins' ); // Relative to ABSPATH. For back compatibility.`
`define( 'WPMU_PLUGIN_DIR', WP_CONTENT_DIR . '/mu-plugins' ); // Full path, no trailing slash.`
`define( 'WPMU_PLUGIN_URL', WP_CONTENT_URL . '/mu-plugins' ); // Full URL, no trailing slash.`
`define( 'MUPLUGINDIR', 'wp-content/mu-plugins' ); // Relative to ABSPATH. For back compatibility.`
`define( 'TEMPLATEPATH', get_template_directory() );`
`define( 'STYLESHEETPATH', get_stylesheet_directory() );`

## Set post revisions to something feasible

`define( 'WP_POST_REVISIONS', 15 );`

## Autosave interval of post revisions in seconds

`define( 'AUTOSAVE_INTERVAL', 160 ); // Seconds`

## Set cookie domain for login cookies

Very helpful if you’re getting cookie errors during login
`define( 'COOKIE_DOMAIN', '.domain.com' ); // Domain and all subdomains`
`define( 'COOKIE_DOMAIN', 'domain.com' ); // only root domain`
`define( 'COOKIE_DOMAIN', 'www.domain.com' ); // only subdomain`

## More cookie constants

`define( 'COOKIEPATH', $_SERVER['HTTP_HOST'] . '/' ); // You should set this explicitly.`
`define( 'SITECOOKIEPATH', $_SERVER['HTTP_HOST'] . '/' ); // You should set this explicitly.`
`define( 'ADMIN_COOKIE_PATH', SITECOOKIEPATH . 'wp-admin' );`
`define( 'PLUGINS_COOKIE_PATH', preg_replace( '|https?://[^/]+|i', '', WP_PLUGIN_URL ) );`

## Cookie names

`define( 'USER_COOKIE', 'wordpressuser_' . COOKIEHASH );`
`define( 'PASS_COOKIE', 'wordpresspass_' . COOKIEHASH );`
`define( 'AUTH_COOKIE', 'wordpress_' . COOKIEHASH );`
`define( 'SECURE_AUTH_COOKIE', 'wordpress_sec_' . COOKIEHASH );`
`define( 'LOGGED_IN_COOKIE', 'wordpress_logged_in_' . COOKIEHASH );`
`define( 'RECOVERY_MODE_COOKIE', 'wordpress_rec_' . COOKIEHASH );`

## WordPress debug on and off

`define( 'WP_DEBUG', true );`
`define( 'WP_DEBUG_LOG', true );`
`define( 'WP_DEBUG_DISPLAY', true );`
`define( 'WP_LOCAL_DEV', true ); // Magic switch for local dev`

## Script and style debug

`define( 'CONCATENATE_SCRIPTS', false ); // Causes WordPress scripts to be included separately`
`define( 'SCRIPT_DEBUG', true ); // Uses unminified scripts`
`define( 'SAVEQUERIES', true ); // Requires analyzing the global $wpdb object.`
`define( 'COMPRESS_SCRIPTS', true );`
`define( 'COMPRESS_CSS', true );`
`define( 'ENFORCE_GZIP', true );`

## Disable WP cron in favor of server cron

`define( 'DISABLE_WP_CRON', true );`
`define( 'ALTERNATE_WP_CRON', true ); // alternate method of firing cron in the background when initiated by end users.`
`define( 'WP_CRON_LOCK_TIMEOUT', MINUTE_IN_SECONDS ); // limit cron runs to a certain interval.`

## SSL

`define( 'FORCE_SSL_LOGIN', true ); // Only secure the registration/login process`
`define( 'FORCE_SSL_ADMIN', true ); // Force SSL for the whole WordPress admin`

## The “timthumb” fix

`define( 'WP_HTTP_BLOCK_EXTERNAL', true );`
`define( 'WP_ACCESSIBLE_HOSTS', 'api.wordpress.org,*.github.com' ); // Only allow particular hosts in`

## Modifying files

`define( 'DISALLOW_FILE_EDIT', true ); // Kill the WordPress file editor`
`define( 'DISALLOW_FILE_MODS', true ); // Don't allow users to update core, plugins, or themes`
`define( 'IMAGE_EDIT_OVERWRITE', true ); // Allow editing images to replace the originals`

## Changing WordPress updates

`define( 'AUTOMATIC_UPDATER_DISABLED', true ); // Disable all WordPress auto-updates`
`define( 'WP_AUTO_UPDATE_CORE', false ); // Only disable core updates`
`define( 'WP_AUTO_UPDATE_CORE', 'minor' ); // Only enable minor core updates`

## Change languages

`define( 'WPLANG', 'de_DE' );`
`define( 'WP_LANG_DIR', dirname(__FILE__) . 'wordpress/languages' );`

## Trash

`define( 'EMPTY_TRASH_DAYS', 30 ); // Number of days to wait before emptying the trash`
`define( 'MEDIA_TRASH', false ); // Whether to allow media items to use the trash functionality.`

## Dev tools

`define( 'SHORTINIT', false ); // Disable most of WordPress. Useful for fast responses for custom integrations.`
`define( 'WP_USE_THEMES', true ); // Override if you love WordPress, but hate themes. @credit: https://wordpress.stackexchange.com/questions/12919/what-is-the-constant-wp-use-themes-for`

## Recovery mode and fatal error handling

`define( 'WP_SANDBOX_SCRAPING', true ); // Turn off WSOD Protection (and don't send email notification)`
`define( 'WP_START_TIMESTAMP', microtime( true ) ); // Modify the WordPress start time.`
`define( 'RECOVERY_MODE_EMAIL', '[[email protected]](/web/20240304154809/https://wpclouddeploy.com/cdn-cgi/l/email-protection)' ); // Set a recovery mode email.`

## Fancy stuff

We found these by scouring Google to find more constants.

#### User & Meta Tables

define( 'CUSTOM\_USER\_TABLE', $table\_prefix.'my\_users' );
define( 'CUSTOM\_USER\_META\_TABLE', $table\_prefix.'my\_usermeta' );

Official Docs for these: [Custom User & Meta Tables](https://web.archive.org/web/20240304154809/https://developer.wordpress.org/apis/wp-config-php/#custom-user-and-usermeta-tables)

## Official WP Docs

Here is a link to the [official WordPress WP-CONFIG documentation](https://web.archive.org/web/20240304154809/https://developer.wordpress.org/apis/wp-config-php/)

- - -

Credit for most of this list goes to Mike Garrett: [https://gist.github.com/MikeNGarrett/e20d77ca8ba4ae62adf5](https://web.archive.org/web/20240304154809/https://gist.github.com/MikeNGarrett/e20d77ca8ba4ae62adf5)

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240304154809/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
