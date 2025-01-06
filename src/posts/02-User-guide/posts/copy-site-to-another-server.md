---
title: "Copy Site To Another Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Copy Site To Another Server
  parent: 02-User-guide
  order: 10
---
You can copy a site from one server to another server. Once the site is on the new server you can change the domain name if you wish.

_Important: **You should only copy the same site to a target server ONCE.** If you do it again, the original copy will get overwritten. This is because the tables, database name, users etc are the same as the original site. Copying the site again to the same target server will overwrite any changes you have made on the target server for the prior copy of that site._

To copy a site to a new server:

*  Go to DevelopVIDeploy → Applications
*  Click on the site for which this action will apply
*  Click on the _Copy To Server_ tab
*  There should only be a single section on this screen. Select your target server from the drop-down list of servers.
*  Click the _Copy To Site_ button
*  Click the _OK_ button in the confirmation window

A popup will appear that will offer periodic feedback as the cloning process progresses.

When the process is complete you will get a popup confirmation message and the black ‘terminal” window will show the actions that were taken while copying the site. You can also see this information in the _COMMAND LOG_ screen.

## Before Copying A Site

Please make sure that there is enough disk space on both the current server and the target server to clone the site. We recommend at least TWICE the space as the site currently occupies:

For example, if the site is 100MB, then you need an additional 100MB on the current server and 200MB on the target server. This is because the files are compressed into an archive before being copied to the target server. So you need space on the current server to compress the files and then you need space on the target server to decompress them.

If the copy fails because of a lack of disk-space, your new site might be left in an undefined state and you will need to use our PAID support resources to help you clean up the site on your server.

## Copying Large Sites

When copying large sites, you might see some “file not found” errors in the terminal. This is because it is taking a very long time to copy the files and, while that is happening, there is no output being sent to the log files.

If you know that your site is large then you should be patient and let the process run for a bit pass all those error messages.

## sFTP Users

We attempt to push your sFTP users for the site to the target server. However, if you have two sites on different servers with the same user name, things could get wacky on the target server. So, as a best practice, consider having unique names for your sFTP users across all your sites on all your servers. This way when you start pushing things around you don’t end up with user names that step on each other.

## Other Notes

With this feature there are a few significant caveats:

*  _If you are copying the same site multiple times to the same server, make sure you DELETE the existing site from the target server prior to starting the copy operation. You can do this using the REMOVE SITE option under the MISC tab for the app on the target server. **If you do not do this, you could end up with duplicate APP records on the target server.**_
*  You cannot a site from a server running NGINX to one running OPENLITESPEED or vice versa.
*  Many of the caveats mentioned in our [SERVER SYNC documentation](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-addons-and-upgrades/server-sync-notes/) for that feature apply here so make sure you read that!
*  As mentioned at the top of this document, If you copy a site once and then copy it again, the original copy will get overwritten This is because the tables, database name, users etc. are the same as the original site. Copying the site again to the same target server will overwrite any changes you have made on the target server for the prior copy of that site.
*  If your private keys for the root/sudo user is protected by a password, you cannot use the copy to server function. This is because the communication between the two servers is automated and there is no human interaction that will allow the private key password to be provided.
*  If you have server sync enabled, make sure that you don’t choose a destination that is SERVER SYNC server as the target server!
*  We strongly suggest that you clear the OBJECT CACHE (such as MemCached or REDIS) if it’s enabled on the target server.
*  You can only copy sites between servers that have a ‘root’ login. SUDO logins such as ‘ubuntu’ will not work (which means that you cannot copy sites between servers for providers such as AWS and GOOGLE CLOUD)
*  Verify sure your destination server is cleared to accept incoming connections from your source server – sometimes admins create a firewall on servers and forget that they did that.

- - -

## Issues

- - -

### NGINX Web server fails to restart on the target server after a site is copied.

You might see the following messages in the logs after a site is pushed to a new server:

Job for nginx.service failed because the control process exited with error code.
See "systemctl status nginx.service" and "journalctl -xe" for details.
Site Sync Completed Successfully.

This means that the site has been copied but there is now a conflict in the NGINX configuration files that prevents the server from being started.

Usually, this problem is because of a long-standing conflict between NGINX, CERTBOT and IPV6. (CERTBOT is the service responsible for issuing SSL certificates.)

The short story here is that NGINX only wants one IPV6 statement in its configuration files across all sites. And CERTBOT is smart enough to know this and will make sure that only one site has this configuration item enabled. BUT, when you push a site to the new server, CERTBOT knows nothing about this. So it is possible that the site you pushed has this item in it which will conflict with any existing sites on the target server that also has this configuration item in it.

So, the fix is as follows:

1.  ssh into your server
2.  Navigate to _/etc/nginx/sites-enabled_.
3.  Edit the configuration file for the site you just pushed – eg command to edit a site named “mydomain.com”: _nano mydomain.com_.
4.  Scroll down to the line that has this item on it: listen \[::\]:443 ssl **ipv6only=on**; # managed by Certbot
5.  Remove the _**ipv6only=on**_ text.
6.  Save the file.
7.  Start NGINX with this command: _service nginx start_.

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240529140205/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
