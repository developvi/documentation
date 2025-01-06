---
title: "Action Hook dvi_command_wordpress-app_completed_after_cleanup"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Action Hook dvi_command_wordpress-app_completed_after_cleanup
  parent: 05-Developers-Notes
  order: 17
---
do_action( "wpcd_command_{$this->get_app_name()}_completed_after_cleanup", $id, $app_id, $name, $base_command )

This is a variable action hook whose name changes based on the status of the command being run. See discussion below for more information.

### **Example Hook**
```php
add_action( "wpcd_command_wordpress-app_completed_after_cleanup", 'my_function', 10, 4 );
public function my_function( $id, $app_id, $name, $base_command ) {
      //your code here
}
```

### Discussion

This hook is fired after any long-running command is completed and after metas in the associated app records have been removed. Long running commands are actions like deploying servers and websites (the ones that usually include the black ‘terminal’ screen.)

The name of the hook depends on the app name being run. For WordPress actions, the app name will always be _wordpress-app_.

Unless you want to run an action after every single long-running command, you should check the $name or $base_command variable and base your code on the result of that check.

**If you are looking to perform actions after a WordPress site is deployed, this is likely the hook you need.**

*   **$id** is the post_id of the SERVER custom post type record.
*   **$app_id** is the post_id of the APP custom post type record.
*   **$name** is the name of the command being run but it can also include a random number unique to the current process.
*   **$base_command** is the command name such as _change_domain, prepare_server_ or _install_wp_.

### Reference

Located in:

*   Function: command_completed
*   File: _/includes/core/apps/wordpress-app/traits/traits-for-class-wordpress-app/commands-and-logs.php_

### Other Notes

This hook is used in our [_WOOCOMMERCE_](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/downloads/sell-wordpress-site-subscriptions-with-woocommerce/) add-on to install SSL after a site is deployed.

### Availability

_This hook is only available in DVI versions 4.2.5 or later._

### More Topics In Dev Notes

*   [Filter Hook: wpcd_script_file_contents](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By wpcd](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_completed](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes_wc](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240529141741/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
