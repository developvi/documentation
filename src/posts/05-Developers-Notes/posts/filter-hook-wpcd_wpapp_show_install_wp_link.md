---
title: "Filter Hook wpcd_wpapp_show_install_wp_link"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Filter Hook wpcd_wpapp_show_install_wp_link
  parent: 05-Developers-Notes
  order: 3
---
apply\_filters( 'wpcd\_wpapp\_show\_install\_wp\_link', true, $post\_id )

This filter is used to show or hide the “Install WordPress” link that shows up when you hover over a WordPress server on the server list. It’s used primarily by the [Server Sync](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/downloads/server-sync/) add-on to remove the link from destination servers.

### More Topics In Dev Notes

*   [Filter Hook: wpcd\_script\_file\_contents](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd\_wpapp\_show\_install\_wp\_button](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd\_settings\_help\_tab\_text](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd\_settings\_welcome\_text\_initial](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd\_settings\_welcome\_text](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd\_settings\_deploy\_first\_wp\_site\_text](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By DVI](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd\_server\_wordpress-app\_server\_created](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd\_server\_wordpress-app\_prepare\_server\_command\_done](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd\_command\_wordpress-app\_completed](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd\_command\_wordpress-app\_prepare\_server\_completed](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd\_wordpress-app\_initial\_server\_attributes](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd\_wordpress-app\_create\_popup](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd\_wordpress-app\_install\_app\_popup](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd\_wordpress-app\_initial\_server\_attributes\_wc](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd\_wordpress-app\_install\_wp\_app\_parms](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd\_command\_wordpress-app\_completed\_after\_cleanup](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240419235507/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
