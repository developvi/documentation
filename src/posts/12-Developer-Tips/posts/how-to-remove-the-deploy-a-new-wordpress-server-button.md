---
title: "How To Remove The DEPLOY A NEW WORDPRESS SERVER Button"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Remove The DEPLOY A NEW WORDPRESS SERVER Button
  parent: 12-Developer-Tips
  order: 4
---
There are situations where you might need to remove the DEPLOY A NEW WORDPRESS SERVER button from your users screens. We’re talking about removing this button:

[![](https://web.archive.org/web/20240529160940im_/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-how-to-remove-the-deploy-a-server-button-01.png)](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-how-to-remove-the-deploy-a-server-button-01.png)

This is one of those cases where it’s deceptively simple – no code needed. You just need to remove a particular capability for the users role.

Using your favorite ROLES and CAPABILITIES plugin (our favorite is [USER ROLE EDITOR](https://web.archive.org/web/20240529160940/https://wordpress.org/plugins/user-role-editor/)), remove the _wpcd\_provision\_servers_ capability for the users role:

[![](https://web.archive.org/web/20240529160940im_/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-how-to-remove-the-deploy-a-server-button-02.png)](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/wp-content/uploads/2022/03/wpcd-how-to-remove-the-deploy-a-server-button-02.png)

## Related

*   [Learn more about DVI capabilities](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/).
*   Learn about the the [interplay between Roles, Capabilities, Teams, Authors and Owners](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/teams-vs-owners-authors-vs-roles/).

### More Topics In Developer Tips

*   [Using Visual Studio Code With DevelopVIDeploy](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/documentation/developer-tips/using-visual-studio-code-with-wpclouddeploy/)
*   [How To Make Edits Directly In Core Files And Not Lose Changes On Upgrades](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/how-to-make-edits-directly-in-core-files-and-not-lose-changes-on-upgrades/)
*   [Add Custom Search Fields To The App (Site) List](https://web.archive.org/web/20240529160940/https://wpclouddeploy.com/documentation/developer-tips/add-custom-search-fields-to-the-app-site-list/)
