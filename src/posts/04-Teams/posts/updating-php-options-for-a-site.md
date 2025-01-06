---
title: "Updating PHP Options For A Site"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Updating PHP Options For A Site
  parent: 04-Teams
  order: 5
---
Starting in Version 4.0.0 of DVI, we introduced a new team option that specifies whether a team member can add or update PHP specific options. This locks down a potentially vulnerable area because certain PHP options can provide server-wide access.

With this new option the default is to allow only WP ADMINS and SUPER ADMINS to set PHP options for a site. This, as you might expect, can be changed by assigning the permission to particular teams. However, for installations prior to version 4.0.0, this option will not show up in the TEAMS screens. This can be forced to be visible as follows:

1.  Enable the PERMISSION LIST menu item
2.  Add the new permission to the PERMISSION LIST
3.  Update designated teams access to the new item

More details about each of the above listed steps are below:

## 1\. Enable the PERMISSION LIST menu item.

To enable the PERMISSION LIST menu item, you need to add the following entry to your wp-config.php file:

define('WPCD\_SHOW\_PERMISSION\_LIST', true);

## 2\. Add The New Permission to the PERMISSION LIST

*   Go to WPCLOUD DEPLOY -> PERMISSION LIST
*   Click the ADD SERVER/APP PERMISSION button at the top of the screen
*   For the title enter _Update Site PHP Options_
*   For _Object Type_, set it to APP
*   For _Permission Name_, enter _wpapp\_update\_site\_php\_options_
    *   NOTE: all lower-case!
*   For Permission Category, choose _wpapp_.

Click the PUBLISH button.

[![](https://web.archive.org/web/20240420002641im_/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpclouddeploy-136.png)](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/wp-content/uploads/2020/10/wpclouddeploy-136.png)

## 3\. Update designated teams access to the new item

Now you can use the WPCLOUD DEPLOY -> TEAMS menu option to assign this permission to your teams.

## 4\. (Optional) Remove the PERMISSION LIST menu item

You can now remove the PERMISSIONS LIST menu item by removing the wp-config.php entry that was added in step 1 above.

### More Topics In Teams and Security

*   [Introduction To Teams](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/introduction-to-teams/)
*   [Preparing Users for a Team](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/preparing-users-for-a-team/)
*   [Creating Teams](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/creating-teams/)
*   [Assigning Teams](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/assigning-teams/)
*   [Roles and Capabilities](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/)
*   [Teams, Owners, Authors & Roles](https://web.archive.org/web/20240420002641/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/teams-vs-owners-authors-vs-roles/)
