---
title: "Health Column Messages"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Health Column Messages
  parent: 06-Troubleshooting-and-FAQs
  order: 8
---
We show a variety of warning messages in the server HEALTH column as needed. Most are simple warnings but some of them are important and need to be handled quickly.

**Keep in mind that the messages in the health column only update ONCE every evening.** Thus, even when you resolve an issue, you might not see messages updated or removed from the column right away. You can force an update sooner by scheduling callbacks to run using the options under the **CALLBACKS** tab for the server.

- - -

## Message: The default PHP server version is incorrect

The default PHP server version is what’s used to run wp-cli. WP-CLI is an integral part of your WordPress server infrastructure. If it fails to run properly you will not be able to perform common actions such as changing your domain and cloning sites.

The correct PHP version to use is a little tricky. This is because not all plugins and themes are yet fully compatible with PHP 8.x. Even the ones that state they are compatible still throw deprecation warnings into the WP error logs.

If you know that all your plugins and themes do not throw errors with PHP 8.x, you can set the default server PHP version to 8.1 or 8.2. Even PHP 8.0 no longer receives security updates!

However, for maximum compatibility you can use 7.4 – most plugins and themes were updated to be compatible with this version years ago. Note that 7.4 is no longer receiving security updates though; so if you can, it’s best to use 8.1 or 8.2

You can change the default PHP version for a server using the TOOLS tab for the server.

- - -

## Message: Updates Check Error Notice: Please run all updates manually

[![](https://web.archive.org/web/20240529160404im_/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-health-messages-01.png)](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/wp-content/uploads/2023/02/wpcd50-health-messages-01.png)

This message shows up when we’re unable to get a count of the number of updates needed for a server.

To resolve it, you usually have to run ALL server updates from the command line. When the updates are complete, you then need to restart the server.

While you can attempt to run the updates from the DVI Server **UPDATES** tab, there is no guarantee that they will work – the best way to run them to resolve this message is to do so from the command line.

- - -

## Message: _Non Sec. Updates: NNN_

This is a count of the number of non-security related updates available.

In the image example in the prior section above, you see the message: **Non Sec. Updates: 23**

These are usually optional updates and are best run from the command line.

While you can attempt to run these updates from the DVI Server **UPDATES** tab, some of them might require user input so it’s best to run them from the command line whenever possible.

- - -

## Related Articles

*   [Everything You Need To Know About Managing Linux Updates in DevelopVIDeploy](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)

- - -

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [App Summary and Server Action Column Messages](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/app-summary-and-server-action-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
*   [Ubuntu 24.04 Notes](https://web.archive.org/web/20240529160404/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-24-04-notes/)
