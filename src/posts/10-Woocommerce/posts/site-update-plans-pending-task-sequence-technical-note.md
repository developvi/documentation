---
title: "Site Update Plans Pending Task Sequence Technical Note"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Site Update Plans Pending Task Sequence Technical Note
  parent: 10-Woocommerce
  order: 8
---
When an UPDATE PLAN is being run, you should expect the following sequence in the pending task screen:

*   execute-update-plan-push-template-to-server: ready – owner is the template server
*   execute-update-plan-push-template-to-server: in-process – owner is the template server
*   execute-update-plan-get-data-after-push-template-to-server – not-ready – owner is the target server where a copy of the template has been pushed.
*   execute-update-plan-push-template-to-server: complete – owner is the template server and the template has been copied to the target server where sites will be updated.
*   execute-update-plan-get-data-after-push-template-to-server – complete- owner is the target server where a copy of the template has been pushed. domain is being changed on the template copy to a new domain
*   execute-update-plan-get-data-after-template-domain-change – not-ready – owner is the target server where the template is being pushed
*   execute-update-plan-get-data-after-template-domain-change – ready – owner is the target server where the template is being pushed – domain has been changed on the template copy to a new domain.
*   execute-update-plan-get-data-after-template-domain-change – complete – owner is the target server where the template is being pushed – domain has been changed and target sites on the server are being loaded into the pending tasks table for update.

You will see the above sequence for each server being affected. Once a server has been handled, the following sequence should appear for each site on the server.

*   execute-update-plan-update-site-files – ready – owner is the site being updated
*   execute-update-plan-update-site-files – in-process- owner is the site being updated – files are being copied from template clone to the target site. There will be one of this for each site on the server.
*   execute-update-plan-get-data-after-update-site-files – not-ready – owner is the cloned template site.
*   execute-update-plan-update-site-files – complete – owner is the site being updated
*   execute-update-plan-get-data-after-update-site-files – complete – owner is the cloned template site.

- - -

## More Information

[Admin: Site Update Plans](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)

### More Topics In Dev Notes

*   [Filter Hook: wpcd\_script\_file\_contents](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd\_wpapp\_show\_install\_wp\_button](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd\_wpapp\_show\_install\_wp\_link](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd\_settings\_help\_tab\_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd\_settings\_welcome\_text\_initial](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd\_settings\_welcome\_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd\_settings\_deploy\_first\_wp\_site\_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By wpcd](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd\_server\_wordpress-app\_server\_created](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd\_server\_wordpress-app\_prepare\_server\_command\_done](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd\_command\_wordpress-app\_completed](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd\_command\_wordpress-app\_prepare\_server\_completed](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd\_wordpress-app\_initial\_server\_attributes](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd\_wordpress-app\_create\_popup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd\_wordpress-app\_install\_app\_popup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd\_wordpress-app\_initial\_server\_attributes\_wc](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd\_wordpress-app\_install\_wp\_app\_parms](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd\_command\_wordpress-app\_completed\_after\_cleanup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
