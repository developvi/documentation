---
title: "Troubleshooting The “Critical Cron” Email And Related Message Alerts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Troubleshooting The “Critical Cron” Email And Related Message Alerts
  parent: 06-Troubleshooting-and-FAQs
  order: 9
---
DevelopVIDeploy uses a lot of WP CRON jobs to manage things for you. Therefore we also have a mechanism to check to make sure that the CRON jobs are running on a regular basis. If we detect that they are not running we send an email to the site admin and add an alert to the top of the wp-admin area.

However, there are times when you might receive these alert emails and they turn out to be false positives. You’ll know that this is the case when you login to troubleshoot, and realize that all your CRONS are running.

If that’s the case, here are a couple of things to check:

1.  Did you recently run any plugin updates (even non-DVI updates)? If so, then it’s possible that it took longer to run the updates than our check interval so it appeared that the CRONS were not running. In this case you should only get the email once (until you run updates again).
2.  Are you running the REDIS object cache with the site? If so it is possible that the cache is ‘stuck’ and isn’t clearing transients properly when we delete them. If this is the case, turning off the cache should resolve the issue. If it does then you’ll know this is the root cause of the false positive issue.
3.  If you do frequent automatic plugin updates to your site, you’re likely to run into the issue. This is because of the way WordPress CRONS work in conjunction with smaller CRON intervals (1 minute). When WordPress runs automatic updates it puts the site into maintenance mode which can interrupt any CRONS that are running. Because they’re interrupted, they are not allowed to reset themselves which removes them from the CRON scheduler. A good practice would be to deactivate and reactivate DVI to re-register all CRONS after running automatic updates.

- - -

If it turns out that the email is not a false positive you’ll know because when you login there will be a similar warning at the top of the SERVERs and SITE list.

Here are some ideas on what might be the underlying cause of the issue:

1.  Double-check to make sure that the option to disable the native WP CRON is active in your wp-config.php file. If it’s not and you also have a LINUX CRON active, the two will conflict thereby causing WP CRON jobs to be dropped.
2.  Please double-check that you have a LINUX CRON enabled and firing at 1 min intervals. As mentioned in item 1 above, the native WP CRON process should be disabled in wp-config.php.

If it turns out that CRON jobs are indeed missing then the simplest resolution is to deactivate all the DVI plugins and re-enable them.

How do you know if CRON jobs are missing? Check out the section below!

- - -

## Core Crons

**If you are not using or [Better DVI Crons](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/) option**, you can use the WP CRONTROL plugin to view which CRON jobs are running on your site. After the plugin is installed you can use the SETTINGS → TOOLS → CRON EVENTS menu option to view the CRON jobs that are scheduled for the site.

To view just the DVI CRON jobs simply use the search field in the upper right of the list to search for ‘dvi’. As of DVI 5.0, there should be six core crons:

[![](https://web.archive.org/web/20240529150719im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-core-crons-01.png)](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-core-crons-01.png)

If you are running our [POWER TOOLS premium add-on](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/downloads/power-tools/) there are additional CRON jobs that are scheduled as well:

[![](https://web.archive.org/web/20240529150719im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-core-and-powerpack-crons-01.png)](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd50-core-and-powerpack-crons-01.png)

- - -

## Turn off The Email Notification

If you keep getting the email notification but they are always false positives, you can turn them off as follows:

*   Go to **WpCloudDeploy** → **SETTINGS** → **MISC** tab
*   Scroll down to the **CRON WARNING EMAILS** section
*   Check the box for **DO NOT SEND CRON WARNING EMAILS**
*   Click the **SAVE SETTINGS** button at the bottom.

- - -

## Use Our “Better Cron” Setup

We have an optional setup that combines WP-CLI and a Linux Cron to **more reliably run the DVI CRON jobs**.

Learn more about it by clicking the button below.

[More About Better DVI Crons](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)

With this option you will NOT see the list of DVI cron jobs inside of regular WP CRON tools such as WPCRONTROL.

However, if you are using this option and you’re still seeing the warning messages or getting the warning emails, then it’s likely because the server on which DVI is install needs to be restarted – something is preventing the Linux Crons from running and a restart usually resolves that issue.

- - -

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [App Summary and Server Action Column Messages](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/app-summary-and-server-action-column-messages/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
*   [Ubuntu 24.04 Notes](https://web.archive.org/web/20240529150719/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-24-04-notes/)
