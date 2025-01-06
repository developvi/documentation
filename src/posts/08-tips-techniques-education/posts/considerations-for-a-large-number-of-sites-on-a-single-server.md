---
title: "Considerations For A Large Number Of Sites On A Single Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Considerations For A Large Number Of Sites On A Single Server
  parent: 08-tips-techniques-education
  order: 5
---
So, you want to place a large number of low-volume sites on a single server. In order to do so there are three factors to take into consideration:

*   Memory
*   CPU
*   Disk Space

By far, the number one factor to take into consideration is memory usage. This is because we set up each site to use a generous amount of memory by default. Which means that you will likely need to modify the amount of memory each site uses in order to place more of them on the same on the same server.

- - -

# Memory (Servers Running NGINX)

- - -

## The Math

When we provision a site, we automatically provide it with two active PHP workers and one spare worker. We allow the number of workers to scale up to 5.

Each worker is given a maximum of 128 MB of memory which means that, with overhead, each worker uses approximately 150 MB of memory. Since 3 workers are always active, up to 450 MB of memory can be consumed by a single site. And that can go all the way up to 750 MB if all 5 workers are used and consuming the maximum amount of memory.

## Consequences

In the real world, on sites with a low volume of traffic, not all PHP workers will be active on each site. And, those workers will likely not be using the maximum amount of memory. So on a 1 GB server, you will likely find that a site might be using as little as 150 MB of memory unless it is flooded with traffic and running scripts that consume a lot of memory.

BUT, if that does happen, Linux will likely kill the process that uses the most amount of memory. Which is not going to be a PHP worker since each one only uses up to 150 MB of memory. Instead, it is likely to kill your database server (MYSQL) or the web server (NGINX).

And that is going to cause all kinds of issues for ALL sites on the server.

Instead it is better to reduce the maximum amount of memory that each site can use.

## Fixes

### Reduce Max Memory Per PHP Worker

To reduce the maximum memory that each PHP worker can use you can set a memory option in PHP.INI. You’ll need to do this for each version of PHP you use as follows:

*   Log into your server using SSH.
*   Using your favorite editor (we recommend nano) open up the php.ini file:
*   sudo nano /etc/php/**7.4**/fpm/php.ini

*   Using your editors’ search function, search for _memory\_limit_. With nano, the key combination for search is CTRL-W.
*   Change the _memory\_limit_ entry to 96M.
*   Save the file.
*   Restart PHP:
*   sudo systemctl restart php7.4-fpm

*   Now, redo the same process for every version of PHP you’re using – replace “7.4” with your version number in the steps above.

Note that these memory limits will not work on sites with WooCommerce or heavy-duty themes or page builders. But then again, those aren’t the kinds of volume sites that are suitable for stuffing dozens into a single server.

And, even with this change, each site still will end up using up to 650 MB of memory if all PHP workers are maxed out. So, the next step is to reduce the number of PHP workers assigned to each site.

### Reduce PHP Workers Per Site

Unfortunately, with this step, you have to do it for each site.

*   Log into your server using SSH.
*   Using your favorite editor (we recommend nano) open up PHP pool configuration file for your site:
*   sudo nano /etc/php/7.4/fpm/pool.d/**your-domain.com.conf**
*   Edit the following five entries and give them new values (new values shown in bold):
*   pm.max\_children = **2**
    pm.start\_servers = **1**
    pm.min\_spare\_servers = **1**
    pm.max\_spare\_servers = **1**

*   Save the file.
*   Now, redo the same process for every site you have in this version of PHP (7.4)
*   Restart PHP:
*   sudo systemctl restart php7.4-fpm

*   Redo the steps for sites running under other versions of php, replace “7.4” with a different version number in the steps above.

With these changes, now each site will use a max of around 260MB of memory.

### Notes

*   If you push sites to a new server or clone sites into a new domain on the existing server, you will need to redo these settings for the new site.
*   Depending on the types of sites you’re hosting, you might even be able to set the maximum memory for a PHP worker to as low as 64MB. But you’ll want to carefully test your sites to see if they can use that little and still provide your customers decent performance.
*   If you want to automatically use these settings for each new site (which you probably do) you can use SITE PACKAGES or modify the site installation scripts.

### Deactivate Unused PHP Versions

If all your sites are running the same version of PHP then you can deactivate unused versions.

You can do this under the SERVICES tab for the server.

Scroll down to the PHP PROCESSES section and click the DEACTIVATE button next to the your unused PHP versions.

### Increase **_server\_names\_hash\_max\_size_** & **_server\_names\_hash\_bucket\_size_**

For some uses cases you might have so many sites on server you will exceed the memory assigned to hash tables that store the site names. In these instances you’ll want to increase their size.

Please see [Server names (nginx.org)](https://web.archive.org/web/20240420005929/https://nginx.org/en/docs/http/server_names.html#optimization) for more information on how to increase the assigned values for these hash tables.

- - -

# Memory (Servers Running OpenLiteSpeed)

- - -

The easiest way to reduce the amount of memory each site uses is to modify the _maxConnections_ and _maxSSLConnections_ in the server level configuration file. This file is located at:

/usr/local/lsws/conf/httpd\_config.conf

Do not set these values too low though. Start with 15 for each item and go up or down from there.

An additional item you can ADD to the file is the _httpdworkers_ limit. To find the number of _httpd workers_ being used you can run the following command:

ps -ef | grep openlitespeed

This will output the main worker and the number of child workers in use – you’ll probably see at least one child worker per cpu. However, you should probably only have a couple of these processes on an 8 core server and only one on servers with fewer cores (reference: see [this entry](https://web.archive.org/web/20240420005929/https://openlitespeed.org/kb/troubleshooting-too-many-lsphp-processes-on-da-when-using-ols/) in the OpenLiteSpeed Forum).

You can limit the workers by adding something like this close to the top of the file:

httpdworkers 2

You can also modify the _maxConnections_ and _maxSSLConnections_ for each site in the site level vhost configuration. This file is located at:

/usr/local/lsws/conf/vhosts/<yourdomain.com>/vhconf.conf

The values in here should not exceed the values in the server level config file.

The total number of lsphp workers will be **maxconnections \* httpdworkers**.

**Note:** If you install the OpenLiteSpeed Console you’ll be able to change these values without needing to use the command line. Just make sure you uninstall the console when you are finished with your tweaks.

- - -

# Disk Space

- - -

For most cloud servers, the next thing you might run up against is disk space IF you enable our backups. This is because we keep a certain number of backups on the local disk.

If your sites uses a lot of disk space then your backups will use a lot of disk space. So you’ll need to limit the number of backups you keep locally for each site by setting the RETENTION DAYS to a low number. Or, you can set it to -1 which will not keep any backups locally (not recommended.)

- - -

## CPU

- - -

It’s easy to overwhelm your CPU even if each site has a very very low volume of traffic. Here’s an example:

Assume each site has Wordfence installed plus a backup plugin. Wordfence will respond to every hit on the site – which includes bots and attacks. That uses CPU. Then, your backup plugin fires at midnight to backup a site. But it also fires on all the other sites on your server because you set them all to backup at the same time. That’s a big oops!

So, think carefully about the processes that are running on your server and WHEN they are running in order to use your CPU resources effectively. Standard practice that is fine for a few sites will not necessarily translate to a server hosting 20 or 30 sites!

- - -

## Database

- - -

Depending on your traffic patterns, you might need to increase the maximum allowed database connections since each web worker or process will be making one or more database connections for database queries and updates.

In this case you would need to modify the following file:

/etc/mysql/mariadb.conf.d/50-server.cnf

Locate the string **‘max\_connections’**. If it exists, uncomment it and increase its value. The default is usually 150 so maybe try increasing to 300 first.

If the string does not exist, add it under the **\[mysqld\]** section of the file.

You can learn more about **max\_connections** in the [MariaDB max\_connections documentation](https://web.archive.org/web/20240420005929/https://mariadb.com/docs/server/ref/mdb/system-variables/max_connections/).

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420005929/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
