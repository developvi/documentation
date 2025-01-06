---
title: "Technical Upgrade Notes For V 5.0.x"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Upgrade Notes For V 5.0.x
  parent: 01-cloud-deploy-core
  order: 12
---
## Introduction

Version 5.0.x of DevelopVIDeploy [includes some major new features](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/whats-new-in-wpclouddeploy-5-0/). As such, there are some minor steps you need to take to upgrade your existing installations.

Please review the items below and follow the instructions in each section.

- - -

## How To Install The New Version

If you have any premium modules installed, you should NOT upgrade from the WordPress automatic updates screen until all DVI premium modules have been deactivated.

The reason for this restriction is the new version of the core plugin will not work with older premium modules (and vice-versa) and will cause fatal PHP errors (aka white screen errors).

Instead you should follow these steps to properly update all premium modules:

*   Deactivate all premium modules
*   Upgrade DVI Core (either by uploading or by using the WP auto-update process)
*   MANUALLY upload and overwrite all the other premium add-ons (you can get the latest files from your account area)
*   Re-activate your premium add-ons

**If you do not follow these steps you WILL trigger a WP fatal white-screen error. This is because the new core version will not work with your older premium modules.**

- - -

## Connection Tests For Providers

After installing the updated DevelopVIDeploy plugin, please head over to the SETTINGS area and look at each of your Providers.

If a provider has a new **TEST CONNECTION** button, you will need to use that at least once before the remaining fields are shown and your providers start working again.

- - -

## AWS S3

The AWS S3 API now requires a default region.

Existing servers should be fine without it but new servers will require this – please make sure you add it to your settings screen. If it’s missing we’ll use US-EAST-1 as the default – which might not be the correct one for your existing buckets!

- - -

## Other

*   The meta that tracks whether the page cache is enabled was renamed from _wpapp\_nginx\_pagecache\_status_ to _wpapp\_pagecache\_status_. The upgrade should occur automatically whenever you view a site in DVI. We’re mentioning it here in case you have custom code that uses the old meta.

- - -

## After Upgrade Tasks

*   Disable and re-enable callbacks for all servers to get the benefits of the latest callback scripts. This will allow servers to push additional data elements introduced in DVI 5.0 to DVI.
*   Disable and re-enable backups for all servers (if you’re using server level backups)
*   If you are using automatically scheduled backups, add an alert to your calendar for two days from now to remind you to download and open the zip files from S3 for your latest backup(s) (to verify that things are indeed being backed up. This is a good alert to have once per month).

- - -

## After Upgrade: Recommended (But Optional) Tasks

*   Implement the new, optional, DVI cron triggers – see [Better DVI Crons](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)

- - -

## Next Steps

Important: **If you just upgraded from version 4.x**, you should now follow the instructions in the [5.3 Upgrade Notes](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)!

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Change Domain on Control Plane Server](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/change-domain-on-control-plane-server/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240529150448/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
