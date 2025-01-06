---
title: "Server Sync Introduction"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Server Sync Introduction
  parent: 25-Server Sync
  order: 1
---
Server Sync allows you to copy all the data from all the sites from an origin server to a destination/target server.

This is a premium function that requires an add-on for DevelopVIDeploy.

Once you have obtained the add-on, just install and activate it like you would any other plugin. Note that like all the DevelopVIDeploy plugins, you should NOT network activate it.

## Requirements

*   Your DESTINATION server (the backup server) must be a fresh DVI server with no sites or other operations performed on it.
*   If you have installed the CALLBACK functions on the Destination server you should remove them.
*   Your DESTINATION server must have a root login. This means that it cannot be an EC2, LIGHTSAIL, ALIBABA, AZURE or GCP server.

## How To Set Up Server Sync Between Two Servers

*   Go to the SERVER SYNC tab on your **DESTINATION** server (i.e.: the backup server that will be storing the sites from the primary server.)
*   In the SOURCE SERVERS drop-down select the primary server (i.e.: the server that is the live server)
*   Set an interval time. Recommended no less than 60 minutes. For larger sites / servers increase the time so that there is no risk of overlap between sync attempts.
*   Click the START SETUP button.

If you get an AJAX error, try the operation again. If you get an AJAX error more than once then contact our support team for assistance.

## Configuration After Pairing Servers

After two servers have been paired, you need to make sure that you install your object cache service on the destination server if it’s also installed on the origin. In the latest versions of DevelopVIDeploy REDIS is automatically installed on all servers. However, if you’re using an earlier version you should double-check that your object cache configuration is the same on both servers.

## Verifying that Server Sync is Working

If you would like to verify that the destination server is working you can do the following:

*   Verify that the files exist in the destination server: SSH into it and look in the /var/www folder.
*   Use your local HOSTS file to point the domain to the destination server. When you use your browser to navigate to the domain, it should pick up the site on the destination server. Don’t forget to remove the pointer from your HOSTS file when you are done.

#### Note:

*   In Windows, the HOSTS file is stored in c:\\Windows\\System32\\Drivers\\etc\\hosts
*   In LINUX, the HOSTS file is located in /etc/hosts

- - -

### More Topics In Server Sync

*   [Server Sync: Switching To The Destination Server](https://web.archive.org/web/20240304145236/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-switching-to-the-destination-server/)
*   [Server Sync: Notes](https://web.archive.org/web/20240304145236/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-notes/)
