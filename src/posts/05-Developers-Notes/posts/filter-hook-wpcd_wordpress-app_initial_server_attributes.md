---
title: "Filter Hook wpcd_wordpress-app_initial_server_attributes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Filter Hook wpcd_wordpress-app_initial_server_attributes
  parent: 05-Developers-Notes
  order: 12
---
apply_filters( "wpcd_{$this->get_app_name()}_initial_server_attributes", $attributes, $args );

### **Example Hook**

add_filter( "wpcd_wordpress-app_initial_server_attributes", 'my_function', 10, 2 );
public function my_function( $attributes, $args ) {
    //your code here
}

### Discussion

This hook is fired just before data is passed off to the server creation routine. It’s a great place to take any additional fields you’ve added to the server creation popup screen and insert it into the array of server information that will be stored in the server custom post type record.

*   **$attributes** is an array of server data that will be used to create the server. Do not remove anything from this array. You should only add items to it. Anything added to it will be stored on the server custom post type record.
*   **$args** is an array of data that contains all the fields from the server creation popup screen. If you added any fields to that screen or used your own custom popup screen, you should copy data from this array to the $attributes array in order to get it stored in the server custom post type. This way you’ll be able to access and use it later.

This filter is for servers created in wp-admin only. Servers created using WooCommerce on the front-end have a different filter with much different parameters.

### Reference

Located in:

*   Function: _create_instance_
*   File: _/includes/core/apps/wordpress-app/class-wordpress-app.php_

### Availability

_This hook is only available in DVI versions 4.2.5 or later._

### More Topics In Dev Notes

*   [Filter Hook: wpcd_script_file_contents](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By DVI](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_completed](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes_wc](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240304154212/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
