---
title: "Monit / Healing"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Monit / Healing
  parent: 03-Adminstrator-guide
  order: 17
---
DevelopVIDeploy gives you the option of installing a pro-active monitoring service call [MONIT](https://web.archive.org/web/20240304160527/https://mmonit.com/monit/). It is a lightweight service that can be configured to send you email alerts when certain thresholds on your server have been exceeded. MONIT also has a premium option called [M/Monit](https://web.archive.org/web/20240304160527/https://mmonit.com/) that allows for a central dashboard that consolidates information from all your servers as well as well as allow you to use your mobile devices to monitor your servers on-the-go. If you have a subscription, you can connect your server to it.

Note: Monit & [Monitorx](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/) are two different services used for different things.

## Installing Monit On A Server

*   Navigate to wpclouddeploy Servers and click on one of your servers
*   Click on the **Healing** tab.
*   There are three sections that need to be filled out in order to activate Monit. Only two are mandatory.
*   The first section requires that you provide a domain through which you’ll access the servers’ dashboard. Generally this is just a subdomain of a domain you already control. It also requires that you provide a user id and password to protect access to the Monit dashboard. (**The user name and password must consist of only ALPHANUMERICS. Otherwise MONIT will fail to start with a silent error.)**
*   The second section requires that you set up a connection to your EMAIL server so that alert emails can be sent.
*   The third section is optional – if you have subscribed to the premium M/Monit service you can connect your server to it by entering your private URL to the services’ dashboard.
*   After filling out the data in the three sections, click the INSTALL MONIT button. It shouldn’t take too long for the installation to complete – maybe a couple of minutes.

[![](https://web.archive.org/web/20240304160527im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-052.png)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-052.png)

After installation is complete you will see a new set of options in that tab. And, if your email configuration is correct, you should receive your first couple of email alerts indicating that the Monit service is up and running.

## Activating SSL

Since the data you are transmitting can be sensitive we encourage you to activate SSL. Assuming that you’ve already pointed your DNS to the servers’ ip, you can just click the SSL Status button on the HEALING tab and an SSL certificate will be requested for you.

## Launching The Monit Dashboard

To view the Monit dashboard all you need to do is click the LAUNCH MONIT button.

[![](https://web.archive.org/web/20240304160527im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-053.png)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-053.png)

## How To Use Your Monit Dashboard

Your Monit dashboard should look something like this:

[![](https://web.archive.org/web/20240304160527im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-054.png)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-054.png)

You can click on an individual item in the first column to drill down into it. **_In particular, when you click on an individual item you will be able to see exactly what levels are being monitored and what actions will be triggered at those levels._**

[![](https://web.archive.org/web/20240304160527im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-055.png)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/wp-content/uploads/2020/12/dvi-v4-055.png)

## What We Monitor

When Monit is installed, we set it up with some simple default monitors. The thresholds are set dynamically based on the size of your server.

We have set it up so that a “cycle” is 2 minutes. I.e.: It will check the services every 2 minutes.

### NGINIX (Web Server)

*   If it uses greater than 70% of the CPU for 4 minutes (2 cycles) an alert will be sent
*   If it uses greater than 80% of the CPU for 10 minutes (5 cycles) it will be restarted

### MariaDB (Web Server)

*   If it uses greater than 70% of the CPU for 4 minutes (2 cycles) an alert will be sent
*   If it uses greater than 80% of the CPU for 10 minutes (5 cycles) it will be restarted
*   If it uses greater than 85% of memory for 6 minutes (3 cycles) it will be restarted

### PHP

*   If it uses greater than 70% of the CPU for 6 minutes (3 cycles) an alert will be sent
*   If it uses greater than 80% of the CPU for 10 minutes (5 cycles) it will be restarted
*   If it uses greater than 85% of memory send an alert

### File System

Monitoring only “/”

*   If diskspace being used is greater than 80% an alert will be sent

### System

*   If memory used is greater than 85% for 6 minutes (3 cycles) an alert will be sent
*   If CPU usage is greater than 70% for 4 minutes (2 cycles) an alert will be sent

Note: CPU usage in Monit can exceed 100% – each processor is “100%” so on a dual processor system CPU usage can be 200%. We dynamically scale CPU thresholds based on the number of CPUs detected when Monit is installed. So, on a 2 processor system we will set the CPU alert level to 140% instead of 70%.

## How To Change The Monit Thresholds

You can only customize what Monit is monitoring by directly editing its configuration files on the server.

Learn more about Monit and how to configure it in the [Monit Documentation](https://web.archive.org/web/20240304160527/https://mmonit.com/monit/documentation/monit.html).

There are some [real-world examples](https://web.archive.org/web/20240304160527/https://mmonit.com/wiki/Monit/ConfigurationExamples#mysqld) of configurations for popular services on the M/Monit site as well.

All Monit configuration files are located in the following locations:

*   /etc/monit/monitrc – this is the overall configuration file
*   /etc/monit/conf-available – this folder holds configurations for individual items such as Nginx, MySQL etc.

## Why Is The Tab Called HEALING

We called the tab on the server page “healing” because Monit will automatically restart degraded services. – i.e.: it will attempt to heal a service. This option is set by default for MariaDB, NGINX and PHP.

## Notes

*   If you resize your server up or down, the default monit settings are likely to be inadequate. So, either edit the monit configuration files directly to adjust or uninstall and reinstall monit to get new defaults.
*   Installing Monit might result in a poorer end user experience if your server is constantly running at full throttle. This is because Monit is configured to restart services if thresholds are exceeded for a certain length of time. That, in turn, will cause existing user connections to drop and new connections to be refused during the services’ restart period. If you need your server to be running at full throttle all the time you should remove Monit or edit the configuration files to use higher thresholds for alerts and automatic restarts.
*   The MONIT configuration file is very sensitive to the format of the configuration data provided. We STRONGLY recommend that you only use alphanumerics for most fields (username, password, the first part of email addresses etc.) Otherwise, monit will fail to start with a silent syntax error.

## Availability

The Monit feature first became available in DevelopVIDeploy version 4.2.5.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304160527/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
