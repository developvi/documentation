---
title: "Action Hook dvi_command_wordpress-app_completed"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Action Hook dvi_command_wordpress-app_completed
  parent: 05-Developers-Notes
  order: 10
---
do_action( "wpcd_command_{$this->get_app_name()}_{$status}", $id, $name,$base_command )

This is a variable action hook whose name changes based on the status of the command being run. See discussion below for more information.

### **Example Hook**
```php
add_action( "wpcd_command_wordpress-app_completed", 'my_function', 10, 3 );
public function my_function( $id, $name,$base_command ) {
      //your code here
}
```

### Discussion

This hook is fired after any long-running command is completed. Long running commands are actions like deploying servers and websites (the ones that usually include the black ‘terminal’ screen.)

The name of the hook depends on the status and the app name being run. For WordPress actions, the app name will always be _wordpress-app_. The most common status you use will be _completed_.

Unless you want to run an action after every single long-running command, you should check the $name variable and base your code on the result of that check.

If you are looking to run actions after a server is deployed you can use this hook. This is NOT the hook to use if you need to run actions after a WordPress site has been deployed. For that you should use the [wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/) hook instead.

*   **$id** is the post_id of the SERVER custom post type record. The post id for the related APP is NOT available here. [Use the _wpcd_command_{$this->get_app_name()}_completed_after_cleanup hook_](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/) instead if you need the APP as well.
*   **$name** is the name of the command being run but it can also include a random number unique to the current process.
*   **$base_command** is the command name such as _change_domain, prepare_server_ or _install_wp_.

### Reference

Located in:

*   Function: _update_command_status_
*   File: _/includes/core/apps/class-wpcd-app.php_

### Availability

_This hook is only available in DVI versions 4.2.5 or later._

### More Topics In Dev Notes

*   [Filter Hook: wpcd_script_file_contents](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By DVI](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes_wc](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240304134228/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
