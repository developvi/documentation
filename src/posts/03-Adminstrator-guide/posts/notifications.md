---
title: "Notifications and Alerts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Notifications and Alerts
  parent: 03-Adminstrator-guide
  order: 12
---
## Introduction

The **NOTIFICATIONS** screen contains user friendly notices based on activity from various parts of the plugin. But the most useful are those created by Callbacks – data pushed from the server to the plugin at regular intervals.

These notices include:

*   Power events (server start up, server shutdown)
*   MONIT alerts.
*   Server restart needed
*   Backup start and end
*   Disk space alerts
*   Site Disk Quotas
*   When malware has been detected (if Maldet is installed)

Over time additional notices will be added.

Notices can be pushed as Alerts to any interested party via the following channels:

*   Email
*   Slack
*   Zapier

## Features

*   Each administrator can can choose where to receive push alerts
*   Administrators can restrict the servers and sites for which they will receive push alerts.
*   Administrators can set up multiple destinations for different types of alerts. For example, low priority servers and sites can have their alerts sent to emails while higher priority servers can be pushed to Slack and Zapier.
*   A short-code to allow users to setup alerts using the front-end.

## Setup Global Message Templates

Each destination (Email, Slack, Zapier) can have a different message format for outgoing notifications.

Before notifications can be sent, these templates need to be setup – most admins only set up the email template but, of course, you can setup SLACK and ZAPIER templates as well.

To setup the global message template for emails, navigate to **WpCloudDeploy→ APP:WORDPRESS – SETTINGS → EMAIL NOTIFICATIONS**.

For Slack, it’s a similar path: **WpCloudDeploy→ APP:WORDPRESS – SETTINGS → SLACK NOTIFICATIONS**.

After configuring one or more of these global templates, you can setup individual alert profiles.

[![](https://web.archive.org/web/20240420001629im_/https://wpclouddeployent/uploads/2023/10/wpcd-50-alerts-01.png)](https://web.archive.org/web/20240420001629/https://wpclouddeployent/uploads/2023/10/wpcd-50-alerts-01.png)

## Setting Up An Alert Profile in WP-Admin

You can add an alert profile as follows:

*   Go to the **SERVER ALERTS → PROFILES** screen (note that SERVER ALERTS is a top-level WordPress menu option in wp-admin that is separate from the DevelopVIDeploy menu option.)
*   Click the **New User Notification** button at the top of the screen.
*   Provide a name for the profile and the fill out the rest of the fields.
*   Note: If you leave servers, sites and other selectors blank, you will receive all alerts for those types of items. For example, if you do not make a selection under servers then you’ll receive notifications for all servers for which you have access.
*   Click the **UPDATE** button to save the alert profile.

## Setting Up An Alert Profile On The Front End

You can allow other users to setup alert profiles on the front-end.

First you have to create a new WP page with the _wpcd\_user\_notifications\_form_ shortcode (if it does not already exist).

[![](https://web.archive.org/web/20240420001629im_/https://wpclouddeployent/uploads/2021/03/wpcd-v4-099.png)](https://web.archive.org/web/20240420001629/https://wpclouddeployent/uploads/2021/03/wpcd-v4-099.png)

Then you can add the page to a menu or a link so that your users can navigate to the page to setup their own alerts.

The short-code will render a page that looks like this:

[![](https://web.archive.org/web/20240420001629im_/https://wpclouddeployent/uploads/2021/02/wpcd-v4-083.png)](https://web.archive.org/web/20240420001629/https://wpclouddeployent/uploads/2021/02/wpcd-v4-083.png)

## Overlap With Monit

When you setup Monit (aka Healing), you’re allowed to set up email notifications. If that’s all you need then there is no need to set up additional alerts using the plugin notifications screen. But, if you want to send those Monit alerts to other places such as Slack or Zapier you can now do that.

## Repeated Notifications

You will get some alerts every day. For example, if you have a server that needs to be restarted, a notification is logged every day. So if you’re receiving those types of alerts, you will receive one every day until the server has been restarted.

_There are other times where you might receive multiple alerts for the same event over a two hour period. This happens because we send a notification to our plugin every time a package is updated on the server. Unfortunately, Linux will run updates in a way that cause these alerts to get triggered multiple times instead of just at the start and end of the process._ We do not have a good way around this right now short of removing notifications to DVI when a package has been updated. But those notifications contain valuable information that we need to know about – in particular if a server needs to be restarted. So we cannot remove it.

## Notes

*   There is no guarantee that alerts will be received in the order they were sent. It is possible that you will receive later alerts first followed by earlier alerts. You can blame email or the order in which Zapier triggers their events .

## Availability

This feature is available in DVI Version 4.6.0 or later.

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420001629/https://wpclouddeploytation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
