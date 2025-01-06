---
title: "Creating Teams"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Creating Teams
  parent: 04-Teams
  order: 3
---
Before you can assign users to a team, you must first [prepare them by assigning them proper capabilities or roles](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/preparing-users-for-a-team/).

Then, to add a new team:

*   Go to the WPCLOUD Deploy → Teams screen.
*   Click the ADD TEAM button at the top of the screen.
*   Give the team a name (title)
*   Add your first team member by searching for them in the TEAM MEMBER drop-down box. This should probably be the person you would like to manage the team.
*   Click the TEAM MANAGER checkbox which will automatically assign them all rights.
*   Click the PUBLISH or SAVE button on the right side of the screen.
*   Use the ADD NEW button at the bottom of the first team member to add additional members.

[![](https://web.archive.org/web/20240529155059im_/https://wpclouddeploy.com/wp-content/uploads/2020/05/wpcd-docs-team-01-1.png)](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/wp-content/uploads/2020/05/wpcd-docs-team-01-1.png)

## Important Notes

You can any any user as a team member. BUT, before they can perform any actions they must have the correct [roles/capabilities](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/).

You can grant any user a permission on the team but if they don’t have the capability, they will still not be allowed to perform the action.

### For example:

If a user has been assigned the **DVIAppManager** role and you try to give that user the ability to View Servers, they will not be able to view any servers. This is because the **DVIAppManager** role does not have the _view\_server_ capability. Without the view\_server capability, the **ALL CLOUD SERVERS** menu option will not appear for them.

### More Topics In Teams and Security

*   [Introduction To Teams](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/introduction-to-teams/)
*   [Preparing Users for a Team](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/preparing-users-for-a-team/)
*   [Assigning Teams](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/assigning-teams/)
*   [Updating PHP Options For A Site](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/updating-php-options-for-a-site/)
*   [Roles and Capabilities](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/)
*   [Teams, Owners, Authors & Roles](https://web.archive.org/web/20240529155059/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/teams-vs-owners-authors-vs-roles/)
