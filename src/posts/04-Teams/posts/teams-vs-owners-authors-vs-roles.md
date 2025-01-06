---
title: "Teams, Owners, Authors & Roles"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Teams, Owners, Authors & Roles
  parent: 04-Teams
  order: 7
---
The interplay between Roles, Capabilities, Teams, Authors and Owners can get very confusing. So, lets break it down a bit.

*   **Capabilities** are the fundamental built-in WordPress building block for security. We provide a [number of them](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/) that helps you control which **menu options** are available to users.
*   **Roles** are combinations of WordPress Capabilities – you can create as many roles are you like with any combination of Capabilities. We provide [five pre-built roles](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/). But, because they are based on Capabilities, they also only control which DVI menu options are available to users.

Once a user accesses a menu option, that’s when TEAMS and OWNERS/AUTHORS start to play a role.

An **Owner** is the same as an **Author**. Internally, the Owner is specified in the author field of the Server and Site custom post types we are using to track things. So you’ll see us use the terms “owner” and “author” interchangeably.

An owner will have full admin capabilities over a resource. So a server owner can see all server tabs and view all sites on a server. They can perform all actions on their server and sites.

A site owner can see all site tabs but not necessarily anything on the server. Of course, if a site owner and a server owner is the same user then they can see all site tabs and all server tabs.

A user on a team will be granted specific rights to a server or site resource as specified in the team definition. BUT, if that user happens to be the owner of the site or server resource, then their permissions will usually override those specified in a team. In other words, Owners of a resource are not bound by the limits of the team.

However, starting in DevelopVIDeploy Version 4.13.0, DVI admins can remove certain tabs from all server and site owners. This can be configured under the DevelopVIDeploy → Settings screen. For the tabs that remain visible to server and site owners, access to them still override anything specified on a team.

Finally, anyone considered an ADMINISTRATOR can see everything and none of the security settings will allow you to hide things from an admin (including tabs). An admin is anyone that is tagged as a _super\_admin_ (WP Multisite) or has the _manage\_options_ capability.

If this explanation fails to clear things up for you, just open a support ticket with your questions and we’ll get them answered!

### More Topics In Teams and Security

*   [Introduction To Teams](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/introduction-to-teams/)
*   [Preparing Users for a Team](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/preparing-users-for-a-team/)
*   [Creating Teams](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/creating-teams/)
*   [Assigning Teams](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/assigning-teams/)
*   [Updating PHP Options For A Site](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/updating-php-options-for-a-site/)
*   [Roles and Capabilities](https://web.archive.org/web/20240304150725/https://wpclouddeploy.com/documentation/wpcloud-deploy-teams/roles-and-capabilities/)
