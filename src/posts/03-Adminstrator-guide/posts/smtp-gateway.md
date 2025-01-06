---
title: "SMTP Gateway"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: SMTP Gateway
  parent: 03-Adminstrator-guide
  order: 29
---
DevelopVIDeploy can install an SMTP gateway to make sure that all your emails from all your WordPress sites are sent.

Why do you need to do this?

Because, in most instances, your cloud server service has blocked emails from being sent from your VM. They do this to prevent spam from being sent from the servers which would place their IPs on black-lists and mark them as being risky. Antivirus products will then prevent connection to those IPs which would not be a good thing for anyone.

So, instead, to send email from WordPress you need to either install an SMTP plugin on each site or you can install our SMTP Gateway which can be used to send email for all sites (with some limitations)

Read more about WordPress emails in our article: [How WordPress Emails Work.](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/how-wordpress-emails-work/)

## How Does The Gateway Work?

The DVI SMTP gateway works by connecting your server to your own EMAIL provider (eg: gmail, mailgun, sendinblue, ses etc.) and then sends email through that provider on behalf of your WordPress sites. i.e.: it acts as a gateway between your WordPress sites and your Email provider.

The connection to the provider is made using the same protocol as any other email service – SMTP (Simple Mail Transport Protocol) – which has been around for many decades now.

The gateway needs to be installed on each server.

- - -

## Pre-requisites

Before you attempt to install the gateway, please make sure that you have the following pieces of information from your email service provider.

*   SMTP Server (eg: smtp.yourprovider.com)
*   SMTP Port (eg: 587)
*   User Name
*   Password
*   Sending Domain (eg: yourdomain.com or subdomain.yourdomain.com)

To make sure that this information is correct, you should configure your desktop email program with them first and send a test email. If it sends successfully you can then proceed to installing the DVI SMTP Gateway.

Note that we will always assume an encrypted connection (SSL/TLS) so you don’t have to specify that information.

- - -

## Installation

Installation is done under the SERVICES tab for your server.

*   Navigate to your server in your server list and edit the server (hover over the server name and click the EDIT link that shows up when you hover)
*   Click on the SERVICES tab
*   Scroll down to the EMAIL GATEWAY section
*   Enter the information requested (which you should have already collected and tested as suggested in the pre-requisites section above)
*   Click the INSTALL EMAIL GATEWAY button

[![](https://web.archive.org/web/20240304151413im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-245.png)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-245.png)

## Send A Test Email

After the gateway is installed, a new section will show up under the SERVICES tab titled EMAIL GATEWAY: SEND TEST EMAIL

[![](https://web.archive.org/web/20240304151413im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-246.png)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-246.png)

Just fill out the information requested and click the SEND TEST EMAIL button.

If the test fails you can use the REINSTALL EMAIL GATEWAY button to update the SMTP credentials for your service.

- - -

## Default SMTP Gateway Credentials

If you have a lot of servers, you can set up default credentials on the DevelopVIDeploy->SETTINGS->APP:WORDPRESS – SETTINGS->EMAIL GATEWAY screen.

[![](https://web.archive.org/web/20240304151413im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-247.png)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-v4-247.png)

You can then use the LOAD DEFAULTS button on the EMAIL GATEWAY setup screen to quickly populate the fields with your default smtp credentials.

Note: If you are using WooCommerce to sell server and site subscriptions, you SHOULD NOT want to use this feature. Otherwise your customers will be able to load the defaults and see the data.

- - -

## Updating Credentials

After you install the email gateway you might later want to change the credentials.

To do this, enter your new information in the EMAIL GATEWAY section and then click the REINSTALL EMAIL GATEWAY button.

- - -

## Caveats

Many transactional email services will limit your outgoing emails to the email you validated or the domain you validated with them.

For example, if you validated [\[email protected\]](/web/20240304151413/https://wpclouddeploy.com/cdn-cgi/l/email-protection) and your site tries to send email from [\[email protected\]](/web/20240304151413/https://wpclouddeploy.com/cdn-cgi/l/email-protection), the email will not be sent.

If this is the case, you’ll have no choice but to use an SMTP plugin instead for each site on the server.

Some other services will send using any “from” address your site specifies but your recipient will see something like “Your Name on behalf of yourdomain.com”. At the time we created this document, MAILGUN and GMAIL are two email services that will send emails with any “from” address with a modification to the “From” name in the email header.

If you really want to ensure all your emails end up being sent with the correct domain from each site in the “From” portion of the email, then an SMTP plugin for each site will be your only option.

These days we like the FLUENT SMTP plugin because of the sheer number of options it supports.

- - -

## Why Use The Gateway

Given all the caveats outlined above, you might be wondering why you might use the Gateway. Here are some reasons:

1.  When a new website is created, you might want WordPress to send its regular “new website” email. In this case, it can only be sent if the gateway has been setup since there will be no other sending service enabled on the new site.
2.  It is a convenient way to send emails from all websites on the server if you don’t care about how the “From” section looks to the recipient. For example, development servers.
3.  If all the sites on the server belong to the same domain (eg: yourdomain.com, support.yourdomain.com, documentation.yourdomain.com, landingpage01.yourdomain.com etc.)

- - -

## Other

You might still need to contact your server provider to ask them to open up the email ports for you. Some of them will prevent even the gateway ports from working until you contact them.

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [Server Updates](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240304151413/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
