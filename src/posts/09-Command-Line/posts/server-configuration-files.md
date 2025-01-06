---
title: "Server Configuration Files"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Server Configuration Files
  parent: 09-Command-Line
  order: 7
---
Here are the locations of the most important configuration files on the server.

Sometimes you just need to get down to the command line and tweak some things. Knowing where these files are located will help!

- - -

## NGINX File Locations

- - -

### **Global Configuration**

/etc/nginx/nginx.conf

This is the master configuration file for your entire NGINX server.

### **Individual Site Configuration**

/etc/nginx/sites-enabled/

Each file in there contains the configuration for a single site.

### **Files For Each Site**

/var/www/

One folder for each site is located in this location. This is where WordPress files are installed.

### **PHP Configuration For Each Site**

/etc/php/7.4/fpm/pool.d

This is the PHP configuration for a site.

Note: change ‘7.4’ to match the version of php you’re working with.

### Public SSH Keys For sFTP Site Users

If you add an SSH key for an sFTP user, that key is stored in:

/var/www/**<domain>**/.ssh\_**<username>**/authorized\_keys.

For example, if you have a domain called _wpvix.com_ and an sFTP user named _sftp\_wpvix\_user_, the public SSH key for the user will be stored in:

/var/www/wpvix.com/.ssh\_sftp\_wpvix\_user/authorized\_keys.

- - -

## Open LiteSpeed File Locations

- - -

### **Global vHost**

/usr/local/lsws/conf/httpd\_config.conf

This is the global configuration file for OLS. It also contains the pointers to the individual configuration files for each site.

### **Site vHost Config**

/usr/local/lsws/conf/vhosts/<yourdomain.com>/vhconf.conf

This is the configuration file for a site. This includes some of the PHP configs for each site.

### **Files For Each Site**

/var/www/

One folder for each site is located in this location. This is where WordPress files are installed.

### **Global PHP configuration**

/usr/local/lsws/lsphp${phpver}/etc/php/${phpver2}/litespeed/php.ini

Note: change ${phpver} to 74, 81 etc. and ${phpver2} to 7.4, 8.1 etc (to match the version of php you’re working with.) eg for php 7.4:

/usr/local/lsws/lsphp74/etc/php/7.4/litespeed/php.ini

### Site PHP Configuration

A site’s PHP.INI file is located in:

/var/www/<domain>/.phpini/php.ini

If you do not see a _.phpini_ folder then it means the server or site was created before DVI 5.2. You will need to create this folder and the _php.ini_ file (while logged in as root/sudo). See the [DVI 5.2 technical upgrade notes](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/technical-upgrade-notes-for-v-5-2-x) for more information.

Note: Change <domain> to match your domain name.

### Public SSH Keys For sFTP Site Users

If you add an SSH key for an sFTP user, that key is stored in:

/var/www/**<domain>**/.ssh\_**<username>**/authorized\_keys

For example, if you have a domain called _wpvix.com_ and an sFTP user named _sftp\_wpvix\_user_, the public SSH key for the user will be stored in:

/var/www/wpvix.com/.ssh\_sftp\_wpvix\_user/authorized\_keys

### Site Logs

/var/www/**<domain>**/html/logs

This folder has the following log files for a site:

*   Webserver Access Logs
*   Webserver Error Logs
*   PHP Error Logs

### Webserver Global Logs

/usr/local/lsws/logs

This folder contains logs for the entire web LiteSpeed server.

*   Error Log
*   Standard Output Error Log
*   Restart Log

In most cases though, the relevant logs you’re looking for are likely to be located in the domain-specific folders mentioned above.

- - -

## Locations of DVI Configuration Files

- - -

### Local Backups

~/.wp-backup
or
/root/wp-backup

This is a hidden folder that stores our compressed backup files. When you attempt to restore a site, we pull the files from this folder. If you need to restore from a remote location you can download the remote files into this location.

### Local Backups (Advanced)

~/.wp-backup2
or
/root/wp-backup2

This is a hidden folder. When we attempt to restore a site, we pull the files from this folder. If you need to restore from a remote location you can download the remote files into this location.

### Configuration Backups

/opt/wp-conf-backup

This is the folder that contains the backups of configurations that we make every four hours (if you choose to install this service on your server)

### List of Sites With Linux Crons

/usr/local/bin/wpcron.txt

When you enable the Linux cron for a site, the information about that site is added to this file. Every minute or so we sequentially process the lines in this file to trigger the WP CRON for each site. By using this file we can ensure that multiple cron jobs aren’t conflicting and fighting for resources.

### List of Sites To Be Copied To Another Server (Site-Sync / Copy-To-Server)

/etc/wp-site-sync.conf

When you schedule a site to be periodically pushed to another server, that site information is added to this file. Just as with crons, when it’s time to run the sync process, we run through the list of sites in this file one at. This prevents the sync process from using up too many resources on the server by attempting to run multiple sync processes simultaneously.

- - -

## Git Control Files

- - -

/var/www/$domain/versions/$version - A copy of the files for a particular tag or version.

/var/www/$domain/git-clones/$branch - A copy of the files for a particular branch or tag

The git-clones folder is used when push-to-deploy is triggered with the ‘fetch’ option. Files are pulled from the specified branch and stored there.

- - -

### More Topics In Command Line

*   [Advanced Backups](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [Alias Domains](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
*   [How To Login To Your Server Via SSH](https://web.archive.org/web/20240304134704/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)
