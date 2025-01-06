---
title: "Server Sync Notes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Server Sync Notes
  parent: 25-Server Sync
  order: 3
---
Here are some things to note about Server Sync / Failover

*   Server Sync only syncs the live site data. Existing backup files stored on the server, backup schedules and crons are not synced.
*   Server Sync will not sync custom nginx configuration files in the /etc/nginx/userconfigs folder.
*   Server Sync will not sync changes to php.ini
*   The destination server must allow root access. Thus, AWS servers that uses the “ubuntu” user instead of “root” will not work as a destination or source server; neither will Azure, Alibaba or Google Servers.
*   Server Sync is useful for sites that are primarily ‘brochure’ sites. You should be careful about syncing servers with e-Commerce sites, especially those using the WooCommerce Subscriptions Premium Addon. Otherwise you’re likely to end up with duplicate orders and charges for your customers. This is because [WooCommerce Subscriptions handles all the renewal logic itself](https://web.archive.org/web/20240304155224/https://wpclouddeploy.com/woocommerce-subscription-handling-surprises/) instead of depending on the credit card merchant. Syncing servers means you have two instances of WooCommerce Subscriptions that will evaluate the renewal logic and trigger payments.
*   The APP COUNT on the destination server will show ZERO until you make the destination server the primary server. This is because we do not create separate app records for the sites that are copied to the destination server.

### More Topics In Server Sync

*   [Server Sync: Introduction](https://web.archive.org/web/20240304155224/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-introduction/)
*   [Server Sync: Switching To The Destination Server](https://web.archive.org/web/20240304155224/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-switching-to-the-destination-server/)
