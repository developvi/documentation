---
title: "Technical Upgrade Notes For V 4.3.0"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Upgrade Notes For V 4.3.0
  parent: 01-cloud-deploy-core
  order: 10
---
After upgrading to Version 4.3.0 of DevelopVIDeploy some actions need to be taken on all your existing servers in order to add support for PHP 8.0 and to prevent future errors when we invoke PHP 8.0 specific routines:

*   Disable and re-enable backups. This will update the backup scripts to their new versions.
*   Uninstall and reinstall the REDIS server (if you have it installed on a server). This will add the Redis php 8.0 extension.

## Server Sync

If you are using server syncing, do not configure server sync to push server data from newer servers with PHP 8.0 to older destination servers! You should, instead, create a new destination server which will automatically have PHP 8.0 support installed.

## Site Sync / Pushing Sites To New Servers

Do not push sites using PHP 8.0 to existing destination servers that have not been updated to PHP 8.0

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Change Domain on Control Plane Server](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/change-domain-on-control-plane-server/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240529144109/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
