---
title: "Site Update Plans Pending Task Sequence Technical Note"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Site Update Plans Pending Task Sequence Technical Note
  parent: 05-Developers-Notes
  order: 20
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

*   [Filter Hook: wpcd_script_file_contents](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_script_file_contents/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By wpcd](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_completed](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes_wc](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240304155754/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
\
