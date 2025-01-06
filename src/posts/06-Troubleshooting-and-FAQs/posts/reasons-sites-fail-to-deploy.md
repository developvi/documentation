---
title: "Reasons Sites Fail To Deploy"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Reasons Sites Fail To Deploy
  parent: 06-Troubleshooting-and-FAQs
  order: 2
---
In general, a site should finish deploying within 5 minutes. Here are some reasons that one might fail to deploy properly or look like it’s “stuck”:

- - -

## WP Cron Jobs Are Not Running

Please verify that DVI Cron jobs are running in WordPress. [These jobs are described here](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/).

- - -

## WP REST API Is Blocked

We use the WP REST API to call back from servers and sites into the DevelopVIDeploy plugin. If the WP REST API is blocked then we will not be notified when processes have been completed on servers and sites.

Some reasons that this might be blocked are as follows:

*   Many security plugins try to block the API so please double-check that this option is turned off if you are using one.
*   Some proxies such as CloudFlare might have page rules or other rules that block the WP REST API access. Please double-check that such rules have not been inadvertently added if you’re using such a proxy service.

- - -

## Critical DVI Folders Might Be Blocked

If you’re using DVI on a server that we have not configured for you, then it is possible that a security plugin or other security process is blocking direct access to the plugins/wp-cloud-deploy folder. We download files from this folder to your cloud servers so if this is blocked things will just not work.

Please check the **Firewalls & Proxies** section of our [Requirements Document](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/) for additional information.

- - -

## Other reasons for sites to not deploy include the following:

*   The server where the site should be installed is out of disk space
*   Critical processes on the server where the site should be installed might be stopped (eg: mysql or nginx)
*   Specifying an invalid password
*   Using illegal characters for things such as the domain name (though we do try to catch these for you before you start the install process)

- - -

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240304150619/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
