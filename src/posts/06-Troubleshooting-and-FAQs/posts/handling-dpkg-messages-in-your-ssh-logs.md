---
title: "Handling dpkg messages in your SSH Logs"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Handling dpkg messages in your SSH Logs
  parent: 06-Troubleshooting-and-FAQs
  order: 10
---
Sometimes server commands might fail and when examining your SSH logs you will see a message similar to the following:

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'

To resolve this you need to log into your server with ssh.

[How to log into your server with SSH](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)

Once logged in you can run the command shown in the logs:

sudo dpkg --configure -a

This will usually give you a prompt asking you to make a decision. One example of such a prompt is:

[![](https://web.archive.org/web/20240529145831im_/https://wpclouddeploy.com/wp-content/uploads/2022/08/wpcd-troubleshoot-dpkg-errors-01.png)](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/wp-content/uploads/2022/08/wpcd-troubleshoot-dpkg-errors-01.png)

Usually you want to accept the default but if you have any questions just contact our support team and we’ll help you get the issue resolved.

- - -

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [App Summary and Server Action Column Messages](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/app-summary-and-server-action-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
*   [Ubuntu 24.04 Notes](https://web.archive.org/web/20240529145831/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-24-04-notes/)
