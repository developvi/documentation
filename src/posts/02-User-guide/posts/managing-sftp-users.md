---
title: "Managing sFTP Users"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Managing sFTP Users
  parent: 02-User-guide
  order: 8
---
When you need to access your server, there are three ways you can do it:

1.  Via the SSH command line using your public/private key pair that is assigned to the root or sudo user (the same one in your settings screen).
2.  Via an sFTP client, also using your public/private key pair that is assigned to the root or sudo user (the same one in your settings screen).
3.  Via an sFTP client using a username & password that applies to just a single site.

You already have everything you need to be able to access your site using (1) and (2). However, to access files via sFTP using a user that is restricted to a single site, you first need to setup the user. To setup a user:

*  Go to **DevelopVIDeploy** → **Applications**
*  Click on the site for which this action will apply
*  Click on the **sFTP** tab
*  If this is the first time you’re setting up a user, there will only be a single section – **ADD AN SFTP USER**.
*  Enter a user name and password
*  Click the **Add User** button.

The screen will refresh and you can click the sFTP tab again to see the new user. At this point you should be able to log into the server using this user id and password. Your server address is going to be the IPv4 address of the server connecting over port 22.

## Additional sFTP User Actions

After you have added your first user, additional sections will appear in the _sFTP_ tab.

*  Remove an existing sFTP user
*  Change the password for an existing sFTP user
*  Set a public key for an sFTP user
*  Remove a password for an sFTP user (only for users with a public key)
*  Remove a public key for an sFTP user (only for users with a password)

## Notes

*  An sFTP user (username) can be assigned to one and only one site. If you try to add the same username to another site, you’ll get an error. This leads to some interesting scenarios. For example, if you add a user to a site, delete the site, re-add a site with the same name, you cannot add that user to the new site. This is because the user already exists (it might not have been deleted when the first site was deleted depending on whether certain options have been enabled).
*  When you add a public key for an sFTP user, the option to change the users sftp password will no longer be available. Only the option to completely remove the password access will be visible. If you need to change the password for the user then remove the public key first.
*  If you upload a public key for a user that already has one, the old one will be automatically removed and the new one added. If you’d like to add multiple public keys for a user you can only do so from the command line.

## Related Videos

- - -

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Managing SSL Certificates](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/enable-or-disable-ssl/)
*  [Page Cache](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240529160108/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
