---
title: "Roles and Capabilities"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Roles and Capabilities
  parent: 04-Teams
  order: 6
---
Access to menus are based on WordPress [CAPABILITIES](https://web.archive.org/web/20240304140630/https://wordpress.org/support/article/roles-and-capabilities/).

We provide the following capabilities:

*   **wpcd\_provision\_servers:** Has the ability to create a new server
*   **wpcd\_manage\_servers:** Has access to the servers menu item
*   **wpcd\_manage\_apps:** Has access to the apps menu item
*   **wpcd\_manage\_logs:** Has access to the logs menu items
*   **wpcd\_manage\_settings:** Has access to the settings menu
*   **wpcd\_manage\_groups:** Has access to the server groups and app groups menus
*   **wpcd\_manage\_teams:** Has access to the teams menu.
*   **wpcd\_manage\_all:** Has access to all menu items.

When the plugin is first installed, we add the following roles that utilize these capabilities:

*   **wpcdAdmin**: has all wpcd capabilities listed above plus those of the core WP Author role
*   **wpcdManager**: has all wpcd capabilities listed above except _wpcd\_manage\_teams_**.** It also includes those of the core WP Author role
*   **wpcdSysAdmin**: Has _wpcd\_manage\_servers_ and _wpcd\_manage\_apps_ capabilities plus those of the core WP subscriber role.
*   **wpcdAppManager**: Has _wpcd\_manage\_apps_ capability only plus those of the core WP subscriber role.

- - -

## Notes

Just in case it’s not clear = most ROLES only control whether or not a user can even access a DVI menu item (such as servers or sites).

Once a user is allowed to see a DVI menu item (eg: servers) because they’ve been assigned a suitable role (or WP capability), then the TEAMS logic and rules take over to determine who can actually view individual servers and sites. The only exceptions to this are:

*   A WP ADMIN is allowed to view all servers and sites and
*   The author set on the server or site post is always allowed to see the server or site.

- - -

### More Topics In Teams and Security

*   [Introduction To Teams](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/introduction-to-teams/)
*   [Preparing Users for a Team](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/preparing-users-for-a-team/)
*   [Creating Teams](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/creating-teams/)
*   [Assigning Teams](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/assigning-teams/)
*   [Updating PHP Options For A Site](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/updating-php-options-for-a-site/)
*   [Teams, Owners, Authors & Roles](https://web.archive.org/web/20240304140630/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/teams-vs-owners-authors-vs-roles/)
