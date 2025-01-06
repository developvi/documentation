---
title: "Filter Hook dvi_script_file_contents"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Filter Hook dvi_script_file_contents
  parent: 05-Developers-Notes
  order: 1
---
apply_filters( 'wpcd_script_file_contents', $script_name )

This filter hook can be used to do two things:

1.  Change the contents of the wrapper commands sent to a server
2.  Change the script that a server will load to do a certain task.

The wrapper command scripts look similar to this:

sudo -i -E cd /root &&
sudo -E \\rm -f ##SCRIPT_NAME## &&
sudo -E wget --no-check-certificate -O ##SCRIPT_NAME## ##SCRIPT_URL## &&
export action=##ACTION## domain=##DOMAIN## user=##BASIC_AUTH_USER## pass=##BASIC_AUTH_PASS## &&
sudo -E dos2unix ##SCRIPT_NAME## &&
sudo -E bash ##SCRIPT_NAME##

You can use this filter to point to a file in a different folder that contains a variant of this script. For example, you can add additional commands to be executed after ##SCRIPT_NAME## executes on the server.

sudo -i -E cd /root &&
sudo -E \\rm -f ##SCRIPT_NAME## &&
sudo -E wget --no-check-certificate -O ##SCRIPT_NAME## ##SCRIPT_URL## &&
export action=##ACTION## domain=##DOMAIN## user=##BASIC_AUTH_USER## pass=##BASIC_AUTH_PASS## &&
sudo -E dos2unix ##SCRIPT_NAME## &&
sudo -E bash ##SCRIPT_NAME##
**sudo -E mycustomcommand**

## About ##SCRIPT_URL##

##SCRIPT_URL## is the pointer to the file that does all the real work on the server. When you ask for WordPress to be installed, the filename pointed to by ##SCRIPT_URL## is loaded up from the server where DVI is running to the server where WordPress needs to be installed.

To override this you can replace ##SCRIPT_URL## with a hard-coded pointer to your own version of the same file.

For example, you can hardcode ##SCRIPT_URL## to something like _/html/mydviserver/custom_file.txt_ so that your script is the one that is always executing instead of our script. The only restriction is that your _custom_file.txt_ must have .txt extension AND it must be accessible via a remote wget() command.

sudo -i -E cd /root &&
sudo -E \\rm -f ##SCRIPT_NAME## &&
sudo -E wget --no-check-certificate -O ##SCRIPT_NAME## **_/html/mywpcdserver/custom_file.txt_** &&
export action=##ACTION## domain=##DOMAIN## user=##BASIC_AUTH_USER## pass=##BASIC_AUTH_PASS## &&
sudo -E dos2unix ##SCRIPT_NAME## &&
sudo -E bash ##SCRIPT_NAME##

### More Topics In Dev Notes

*   [Filter Hook: wpcd_wpapp_show_install_wp_button](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_button/)
*   [Filter Hook: wpcd_wpapp_show_install_wp_link](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wpapp_show_install_wp_link/)
*   [Filter Hook: wpcd_settings_help_tab_text](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_help_tab_text/)
*   [Filter Hook: wpcd_settings_welcome_text_initial](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text_initial/)
*   [Filter Hook: wpcd_settings_welcome_text](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_welcome_text/)
*   [Filter Hook: wpcd_settings_deploy_first_wp_site_text](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_settings_deploy_first_wp_site_text/)
*   [Custom Post Types Used By wpcd](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/custom-post-types-used-by-wpcd/)
*   [Action Hook: wpcd_server_wordpress-app_server_created](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_server_created/)
*   [Action Hook: wpcd_server_wordpress-app_prepare_server_command_done](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_server_wordpress-app_prepare_server_command_done/)
*   [Action Hook: wpcd_command_wordpress-app_completed](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed/)
*   [Action Hook: wpcd_command_wordpress-app_prepare_server_completed](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_prepare_server_done/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes/)
*   [Filter Hook: wpcd_wordpress-app_create_popup](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_create_popup/)
*   [Filter Hook: wpcd_wordpress-app_install_app_popup](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-install_app_popup/)
*   [Filter Hook: wpcd_wordpress-app_initial_server_attributes_wc](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_initial_server_attributes_wc/)
*   [Filter Hook: wpcd_wordpress-app_install_wp_app_parms](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/filter-hook-wpcd_wordpress-app_install_app_popup/)
*   [Action Hook: wpcd_command_wordpress-app_completed_after_cleanup](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/action-hook-wpcd_command_wordpress-app_completed_after_cleanup/)
*   [Site Update Plans: Pending Task Sequence Technical Note](https://web.archive.org/web/20240420000727/https://wpclouddeploy.com/documentation/wpcloud-deploy-dev-notes/site-update-plans-pending-task-sequence-technical-note/)
