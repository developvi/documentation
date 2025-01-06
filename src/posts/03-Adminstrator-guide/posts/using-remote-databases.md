---
title: "Using Remote Databases"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Using Remote Databases
  parent: 03-Adminstrator-guide
  order: 28
---
## Introduction

The default database server for new WordPress sites is the local MYSQL / MARIADB server. For most sites, this is more than sufficient. However, you can choose to use a remote database such as AWS RDS, DIGITALOCEAN or VULTR database or even a database server on a custom server.

As long as the site is able to connect to the remote database with a user that has all read, write, create, drop permissions for the database and the remote database is a MYSQL or MARIADB server, there should be few issues with using one.

## Using A Remote Database

Options for connecting to a remote database are under the DATABASE tab for a site.

There are two options:

*   Switch To Remote Database
*   Copy Database – Local To Remote

In most cases you will want to use the COPY DATABASE – LOCAL TO REMOTE option to seed your remote database with a snapshot of the data in the local database.

[![](https://web.archive.org/web/20240304152541im_/https://wpclouddeploy.com/wp-content/uploads/2022/09/wpcd50-remote-database-02.png)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/wp-content/uploads/2022/09/wpcd50-remote-database-02.png)

Once the remote database has been seeded with a copy of the local database you can then use the SWITCH TO REMOTE DATABASE option to complete the switch.

[![](https://web.archive.org/web/20240304152541im_/https://wpclouddeploy.com/wp-content/uploads/2022/09/Snag_573f9359.png)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/wp-content/uploads/2022/09/Snag_573f9359.png)

- - -

## New Sites

New sites will always be installed on the local database server. After installation you can connect them up to the remote server if you like using the two options described in the prior section.

- - -

## Limitations

There are some limitations when using remote databases – primarily because of limited permissions for db users.

When using local databases we usually have full control over the database server including root control. But for remote databases the db user does not usually have this type of high level access.

Some limitations are:

#### Copy To Remote

If you create a remote database and then delete the site, in many cases the remote data is NOT deleted because the user does not have the permissions to drop the database. This presents two issues:

1.  You will have to manually remove the remote database
2.  If you create the same site (or a new site) that uses the same database name, you might end up with unwanted data in the new site that are remnants from the original deleted site.

#### Deleting Sites

If you delete a site connected to a remote database it is possible the database might not be dropped and/or the tables might not be removed if the database user in wp-config.php does not have the proper permissions to drop the database or remove tables.

#### Statistics

On the STATISTICS tab for an app we will not show database space used for remote databases.

#### Restoring Data

In many cases, the remote user does not have the rights to drop a database. Dropping the database is the cleanest way to make sure the old data goes away. But, during the restore process we’ll also attempt to drop individual tables before restoring them. This should, in most cases, result in your restored site having the correct data. But there are still two issues here:

1.  Any tables that are not explicitly referenced in the original backup will NOT be dropped and
2.  If any table has foreign key constraints or trigger constraints that prevents them from being dropped, we will not be able to detect this and you might end up with duplicate data or missing data. Note that core WP does not have FOREIGN KEY constraints or TRIGGER constraints but some plugins will add them (eg: real-time backup plugins).

#### Cloning Sites

Cloning sites will still use the LOCAL database server, not the remote server. Data from the remote server will be cloned to the local server. If you do not have a local server the cloning operation will fail.

#### Staging Sites

Staging sites will still use the LOCAL database server, not the remote server. Data from the remote server will be cloned to the local server. if you do not have a local server the cloning operation will fail.

#### Copy To Server

As with Cloning & Staging, the target database server will be set to local host. If there is no localhost server the operation will fail.

#### Data Transfers

When copying data to remote databases (or from remote databases) as well as when copying data during cloning and staging operations, the following elements might not be copied:

*   Foreign key relationships
*   Triggers
*   Stored Procedures
*   Views

- - -

## Notes

1.  We have tested this feature using the DigitalOcean and Vultr database services. We fully expect other database services to work such as RDS and AZURE but have not completed testing those internally.
2.  For performance reasons we strongly recommend that you establish a local network VPC between your WordPress server and your primary Remote Database server instead of sending the traffic across the internet.
3.  For the same reasons, we recommend that your database server provider and WordPress server provider are the same and that both servers are in the same region or availability zone.

- - -

## Easy Mistakes

It is going to be very easy to make certain kinds of mistakes. Imagine the following scenario:

*   You create a site _yourdomain.com_
*   You configure it to use a remote database
*   You change the domain to _yourproductiondomain.com_
*   You then decided to switch back to the local database but you use the original local database

With this scenario your site will not work because the original local database is still setup for _yourdomain.com_, not _yourproductiondomain.com_.

- - -

## Using Remote Databases On Servers Earlier Than DVI 5.0

Using a Remote Database is a new feature in DVI 5.0. If you decide to setup a remote database connection on a server that was initially deployed with a version of DVI earlier than 5.0 then you must do the following as well:

*   Remove and reinstall callbacks
*   Remove and reinstall backups

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [SMTP Gateway](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304152541/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
