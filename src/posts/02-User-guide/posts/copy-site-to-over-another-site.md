---
title: "Copy Site To/Over Another Site"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Copy Site To/Over Another Site
  parent: 02-User-guide
  order: 11
---
You can push data from one site to another site, overwriting the target sites’ files and database.

Access this option as follows:

*  Navigate to **DevelopVIDeploy → WordPress Sites**
*  Locate the site you would like to push to another site
*  Click on the site’s title to edit the site metadata
*  Click on the **COPY TO EXISTING SITE** tab

In this tab there will be four options:

*  **Copy Everything** – this will copy all files and the entire database to the target site EXCEPT the wp-config.php file. There is an optional FULL SYNC flag that allow you to delete any file on the target site that is not present on the source site.
*  **Copy Database** – this will copy just the database.
*  **Copy Files Only** – this will copy files except designated files and folders. If no file and folder exceptions are set, it will copy all files to the target site (EXCEPT the wp-config.php file).
*  **Copy Partial Database** – this one is an experimental feature so use at your own risk. The idea is that you can copy either designated tables or copy all tables except the designated ones. One of the biggest risks here is that there might be hard relationships set up between tables and/or triggers in the source or target database which will cause partial copies to fail.

## Notes

*  Files on the target site that do not exist on the source site will remain on the target site and will not be deleted. Only if you specify the FULL SYNC option when using the COPY EVERYTHING option will we delete stray files on the target.
*  You can only push to sites on the same server. To push to a site that exists on another server you should copy the site to the target server first using the COPY TO SERVER feature and then use this feature to push the data to the target site.
*  If there is not enough disk space to take a local backup of the target site, the copy will be aborted. Free space on the disk must be twice the size of the space used by the site.

There are some other situations that can cause this feature to fail. If plugins or themes have added relational rules to your database or triggers that enforce certain conditions, those conditions might not exist as we copy individual tables and replace them. In that case the only option is to completely replace the database on the target site using a backup/restore tool. OR you can create a custom DVI plugin extension to handle the replacement table rules specific for these sites.

- - -

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Staging Sites](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240304151026/https://developvideploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
