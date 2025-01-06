---
title: "HTTP/2"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: HTTP/2
  parent: 03-Adminstrator-guide
  order: 30
---
Our HTTP/2 options behave differently depending on whether you’re using an NGINX server or an OpenLiteSpeed web server.

- - -

## NGINX

When using an NGINX web server, HTTP/2 is an option that is only available AFTER SSL is enabled. It will be visible under the SSL tab for sites.

However, there are some important limitations:

*   It is NOT available for WordPress installs that are configured as a MULTISITE
*   It must be turned OFF before changing domains, cloning or copying sites between servers
*   It must be turned OFF before disabling/enabling SSL

You can turn it \[HTTP/2\] on as follows:

*   Navigate to **WpCloudDeploy** → **WORDPRESS SITES**
*   Click the title of the site you need to operate on
*   Click the **SSL** tab
*   Click the **HTTP/2** toggle switch

## OpenLiteSpeed

When using an OpenLiteSpeed web server, HTTP/2 is automatically enabled and disabled when SSL is enabled/disabled.

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [Root User Passwords](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Change Domain on Control Plane Server](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/change-domain-on-control-plane-server/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240529155954/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
