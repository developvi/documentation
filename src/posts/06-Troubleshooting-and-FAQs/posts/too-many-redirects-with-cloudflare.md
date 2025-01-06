---
title: "Too Many Redirects With CloudFlare"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Too Many Redirects With CloudFlare
  parent: 06-Troubleshooting-and-FAQs
  order: 4
---
If you use Cloudflare in front of your sites, it is possible that you can run into a TOO MANY REDIRECTS error when SSL is added to your site.

This is generally caused by an incorrect setting for SSL in Cloudflare.

The Cloudflare SSL item needs to be set to FULL (STRICT) as shown in this image:

[![](https://web.archive.org/web/20240529153338im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/cloudflare-strict-ssl.png)](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/wp-content/uploads/2021/12/cloudflare-strict-ssl.png)

Cloudflare tends to default this setting to FLEXIBLE. Once set to FULL this issue should go away.

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [App Summary and Server Action Column Messages](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/app-summary-and-server-action-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
*   [Ubuntu 24.04 Notes](https://web.archive.org/web/20240529153338/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-24-04-notes/)
