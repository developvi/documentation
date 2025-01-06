---
title: "White Label Colors"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: White Label Colors
  parent: 03-Adminstrator-guide
  order: 22
---
### Introduction

For most users, one of the simplest ‘white-label’ things you can do is change the colors to match your brand (or personal preference). DevelopVIDeploy includes a tab in the SETTINGS area for just such a purpose.

To access it, navigate to **DevelopVIDeploy** → **SETTINGS** → **APP: WORDPRESS SETTINGS** → **WHITE LABEL**

In there, you’ll see two sets of colors – the first set applies to the wp-admin area. The second set applies to the front-end features. However, the things that colors affect on the front-end varies a bit vs what gets affected in wp-admin.

This document will give you an idea of what gets affected in each area:

- - -

## WP-ADMIN Colors

- - -

### Primary Brand Color

*   Color of text on menu tab when tab is selected or hovered upon.
*   Color of Section header text in settings area.
*   Background color of buttons at the top of the site details screen.
*   Color of certain warning or error messages (eg: when an API key is not setup).
*   Color of the WEB SERVER name chiclet at the top of the server details screen.
*   Labels for data at the top of the server details and app details screen.
*   Color of title of cards and section headings in server details and app details screen.
*   Background color of buttons when hovered over.
*   Color of the tooltip icon when hovered over.
*   Color of the APP COUNT link at the top of the server detail screen.

### Secondary Brand Color

*   Color of domain name at the top of the site detail screen.
*   Color or server name, region and provider in the area below the site detail header box.
*   Color of the border and hover background of the count of apps at the top of the server detail screen.

### Tertiary Brand Color

*   Background color of the INSTALL WORDPRESS button (located on the SERVER LIST screen).

### Accent Background Color

*   Default background color for most buttons.
*   Background color of left menu bar in the server and site details screen.
*   Part of the subtle gradient definition used for highlighting the current tab. Applies to servers, sites and settings.

### Alternate Accent Background Color

*   Part of the subtle gradient definition used for highlighting the current tab. Applies to servers, sites and settings.

### Medium Background Color

*   Background color in body area of tab.

### Medium Accent Background Color

*   Border of card used in tabs.

### Light Background Color

This is only currently used for the TEXT color in the GIT ‘chicklet’ status that is shown at the top of a SERVER screen.

[![](https://web.archive.org/web/20240420013600im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-colors-admin-light-background-01.png)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-colors-admin-light-background-01.png)

_Yes, we know, the irony of a ‘background’ color being used for foreground text. It was either this or create yet another color option just use ‘white’. If this gets a lot of complaints we’ll change it to ‘white’._

### Positive Color

*   Generally used where we want to invoke a positive feeling – for example the background color when the PHP version is 8.1 or later.

### Negative Color

*   Generally used where we want to invoke a negative feeling – for example the background color when the PHP version is lower than 8.1.

### Alt Negative Color

*   Generally used where we want to a brighter negative color. Eg: warnings on the server CONSOLE tab or when a server requires a restart.

### White

*   This gives you the ability to change the shade of white used in many areas of the application.

- - -

## Front End Overrides

- - -

### Primary Brand Color

*   Color of text on menu tab when tab is selected or hovered on.
*   Background color of buttons at the top of the site details screen.
*   Color of the WEB SERVER name chiclet at the top of the server details screen.
*   Labels for data at the top of the server details and app details screen.
*   Color of title of cards and section headings in server details and app details screen.
*   Background color of buttons when hovered over.
*   Background color of certain buttons when hovered over on the server and site list screens.
*   (no) Color of the tooltip icon when hovered over.
*   Color of ADMIN LOGIN and VIEW SITE buttons on the app list screen.

### Secondary Brand Color

*   (no) Color of domain name at the top of the site detail screen.
*   (n/a) Color or server name, region and provider in the area below the site detail header box.
*   (no) Color of the border and hover background of the count of apps at the top of the server detail screen.

### Tertiary Brand Color

*   Does nothing for now.

### Accent Background Color

*   Default background color for most buttons.
*   Background color for some buttons on the server and site list screens.
*   Background color of left menu bar in the server and site details screens.

### Alternate Accent Background Color

*   Background color of the entire tabbed section in the site and server detail screens. This encompasses the tabbed area, the header area and the buttons for ALL APPS or ALL SERVERS. _This element of this color feature is not available in wp-admin._
*   (no) Part of the subtle gradient definition used for highlighting the current tab. Applies to servers, sites and settings.

### Medium Background Color

*   Background color in body area of tab.

### White Color

*   Does **NOT** override in left menu bar on server and site pages – that area will use the ‘white’ setting for wp-admin.

- - -

## Custom CSS

As you might expect, you don’t need to use any of our settings to customize colors or other aspects of the UI.

For example, you can use the following CSS in the White Label settings area (or your custom CSS style sheet). This will:

*   Make the data cards square, replacing the rounded edges and
*   Give the borders a different color (black)

.wpcd-wpapp-actions .wpcd-card-group {
    border-radius: 0px;
    border-color: black;
}

- - -

_This document applies to DevelopVIDeploy 5.7 or later_

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420013600/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
