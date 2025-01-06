---
title: "Customizing Front-end Styles"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Customizing Front-end Styles
  parent: 08-tips-techniques-education
  order: 11
---
## Introduction

The front-end grids and lists are easy to style with custom css. There are a number of ways you can apply custom css in WordPress:

*   Some themes expose a CUSTOM CSS editor in the WordPress Customizer.
*   You can use your themes functions file to enqueue a custom css script.
*   You can create a plugin to load a custom css script.
*   There are plugins in WordPress.org that allow you to easily add custom css globally.

We also have a text box in our settings screen (on the WHITE LABEL tab) where you can add custom css.

Below are some examples of what you can do with custom css.

- - -

## Full Width Server and App Grids

The default width for the server and app grid/list is 1400px. But, if your content area for your theme is larger, you can force the grid to occupy the full width.

.wpcd-grid-table-rows .wpcd-grid-table-row {
    max-width: 100% !important;
}

- - -

## Change The Number Of Columns in the Server and App Grids

We set both the server and app grid to use three columns on larger screens. You can force it to a different number (eg: 4).

.wpcd-grid-table .wpcd-grid-table-columns,
.wpcd-grid-table .wpcd-grid-table-rows .wpcd-grid-table-row {
    grid-template-columns: 1fr 1fr 1fr 1fr !important;
}

- - -

## Quick Styles for Dark Mode

.wpcd-grid-table-rows .wpcd-grid-table-row {
    /\* Main Container Background \*/
      background-color: #0D091A !important;
}
.wpcd-grid-table .wpcd-grid-table-cell {
      /\* Background for individual cards \*/
      background-color: #292929 !important;
}
.wpcd-grid-table button {
    /\* Buttons need a lighter color since our default is dark. \*/
    background-color: #E91E63 !important;
}
.wpcd-grid-table {
    /\* Text color needs to be white since our default is dark. \*/
    color: white !important;
}
.wpcd-grid-table .wpcd-server-col-element-label-server\_app\_link {
    /\* Background color on the app count card needs to be dark. \*/
    background-color: #0D091A !important;
}
#wpcd\_public\_wrapper button.wpcd\_action\_install\_app {
    /\* Fix border weirdness in install wordpress button. \*/
      border-color: #E91E63 !important;
}

The end result should be something that looks like this:

[![](https://web.archive.org/web/20231207112404im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-front-end-dark-mode-01.png)](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-front-end-dark-mode-01.png)

- - -

## Combine some things: Two side-by-side rows with three columns

/\* Full width .\*/
.wpcd-grid-table-rows .wpcd-grid-table-row {
      max-width: 100% !important;
      }

/\* Three Columns \*/
.wpcd-grid-table .wpcd-grid-table-columns, .wpcd-grid-table .wpcd-grid-table-rows .wpcd-grid-table-row {
  grid-template-columns: 1fr 1fr 1fr !important;
}

/\* Two rows in a column \*/
.wpcd-grid-table-rows {
    grid-template-columns: 1fr 1fr !important;
}

[![](https://web.archive.org/web/20231207112404im_/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-front-end-dark-mode-05.png)](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/wp-content/uploads/2022/05/wpcd-front-end-dark-mode-05.png)

- - -

## WooCommerce Checkout Styling Tips

If you’re asking for things like site name and other info on the checkout page, here’s a simple set of styles that will help break up the default checkout page a bit better:

/\* DVI custom checkout fields on checkout page.\*/
#wpcd\_sites\_custom\_checkout\_fields\_wrap {
border:solid 1px #EBFAF2;
border-radius:7px;
padding:2em;
background-color:#EBFAF2;
}

This will result in something that looks like this:

[![](https://web.archive.org/web/20231207112404im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-wc-60.png)](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-wc-60.png)

- - -

## Other

*   Front-end styling requires wpclouddeploy 5.0 or later.

- - -

### More Topics In Tips, Techniques & Education.

*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [Increase WordPress Upload Size](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20231207112404/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
