---
title: "Filter Hook wpcd_wordpress-app_initial_server_attributes_wc"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Filter Hook wpcd_wordpress-app_initial_server_attributes_wc
  parent: 05-Developers-Notes
  order: 15
---
apply_filters( "wpcd_wordpress-app_initial_server_attributes_wc", $attributes, $item, $items, $user, $subscription );

### Discussion

This hook is fired just before data is passed off to the server creation routine.

It is triggered only by the _SELL SERVERS WITH WOOCOMMERCE_ add-on. Servers created by the normal DVI screens do NOT trigger this hook.

It’s a great place to take any additional fields you’ve added to the server creation popup screen and insert it into the array of server information that will be stored in the server custom post type record.

*   **$attributes** is an array of server data that will be used to create the server. Do not remove anything from this array. You should only add items to it. Anything added to it will be stored on the server custom post type record.
*   **$item** – the WooCommerce item being purchased.
*   **$items** – All items being puchased (users can sometime purchase more than one item)
*   **$user** – The user making the purchase
*   **$subscription** – data about the subscription.
*   **$args** is an array of data that contains all th

This filter is for servers created when a user is purchasing a server via WooCommerce. **_Servers created in wp-admin have a different filter with different parameters._**

### Reference

Located in:

*   Function: wc_spinup_wpapp
*   File: _/includes/core/apps/wordpress-app/class-wordpress-woocommerce.php_

### Availability

_This hook is only available in DVI versions 4.2.5 or later._

### More Topics In Dev Notes

*   [Filter Hook: wpcd_script_file_contents](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By DVI](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_completed](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240221052134/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
