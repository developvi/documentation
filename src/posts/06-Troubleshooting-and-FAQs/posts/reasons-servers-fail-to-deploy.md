---
title: "Reasons Servers Fail To Deploy"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Reasons Servers Fail To Deploy
  parent: 06-Troubleshooting-and-FAQs
  order: 3
---
In general, a server should finish deploying within 30 minutes. Most, except those from VULTR, should deploy in 20 mins or less.

Here are some reasons that a server might fail to deploy properly or look like it’s “stuck”:

## Keys, Keys, Keys

By far, the number one reason for servers not deploying is an incorrect combination of PUBLIC-PRIVATE SSH keys provided in the SETTINGS screen. Check, double-check and triple-check that your public-private key combinations are correct and that your password for your private key, if any, is valid (and does not contain special characters).

[How to generate SSH key-pairs](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)

If the information for your SSH key-pair is not entered properly we cannot log into the newly provisioned server to install our stack.

## Bad Location & Size Combination

Many providers do not have all server sizes at all locations. VULTR’s High Frequency servers are a particular egregious violator. So, it is possible that you might be requesting a server size that just isn’t available.

## Firewalls & Proxies

When a new server is being provisioned, it needs to call back into the server on which the DVI plugin is installed. If that server has a firewall in front of it, then the call-backs might be blocked. The easiest way to handle this is to white-list your new servers’ IP as soon as it’s finished being created – you’ll need to monitor your server providers’ dashboard to see when the server is up and running and then copying its IP address to white-list on your firewall.

- - -

## WP Cron Jobs Are Not Running

Please verify that DVI Cron jobs are running in WordPress. [These jobs are described here](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/).

- - -

## WP REST API Is Blocked

We use the WP REST API to call back from servers and sites into the DevelopVIDeploy plugin. If the WP REST API is blocked then we will not be notified when processes have been completed on servers and sites.

Some reasons that this might be blocked are as follows:

*   Many security plugins try to block the API so please double-check that this option is turned off if you are using one.
*   Some proxies such as CloudFlare might have page rules or other rules that block the WP REST API access. Please double-check that such rules have not been inadvertently added if you’re using such a proxy service.

- - -

## Critical DVI Folders Might Be Blocked

If you’re using DVI on a server that we have not configured for you, then it is possible that a security plugin or other security process is blocking direct access to the plugins/wp-cloud-deploy folder. We download files from this folder to your cloud servers so if this is blocked things will just not work.

Please check the **Firewalls & Proxies** section of our [Requirements Document](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/) for additional information.

- - -

See also: [Common server deployment issues and error messages](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/wpcloud-deploy/common-server-deployment-issues/)

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240304151631/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
