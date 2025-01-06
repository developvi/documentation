---
title: "Fixing Error 413 REQUEST ENTITY TOO LARGE"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Fixing Error 413 REQUEST ENTITY TOO LARGE
  parent: 08-tips-techniques-education
  order: 8
---
Sometimes when doing large migrations or other activities involving large file uploads, you’ll run into an error message #413 from the web server: REQUEST ENTITY TOO LARGE.

You can attempt to fix this by changing options in your NGINX and PHP configuration files

## NGINX CHANGES

Update the _client\_max\_body\_size_ in your nginx configuration files – from 25M (default) to something larger such as 100M or 250MB.

To do this you will need to ssh into your server:

Once you’re in:

*   Go to the /etc/nginx/sites-enabled folder:
    *   cd /etc/nginx/sites-enabled

*   In there are a series of files for each of your domain. Edit the one for your domain using the NANO editor:
    *   nano _yourdomain.com_

*   About 14 lines down you’ll see the entry for _client\_max\_body\_size._ Change it to whatever you want.
*   Use the CTRL-O key combination to save the file.
*   Use the CTRL-X key combination to exit the editor.
*   Restart the nginx web server with:
    *   service nginx restart


## PHP.INI CHANGES

Update the _post\_max\_size_ entry in your php.ini file – from 25M (default) to something larger such as 100M or 250MB. **You can do this from the DVI site admin screen under the PHP tab**. However, since you might already be in the server, you can change it from the command line as well:

*   Go to the /etc/php/7.4/fpm folder (assuming you’re using PHP 7.4):
    *   cd /etc/php/7.4/fpm

*   Edit the PHP.INI file using the NANO editor:
    *   nano _php.ini_

*   Scroll down until you see the _post\_max\_size_ entry (or use the CTRL-W key combination to enter a search term.)
*   Change its assigned value from 25M to something larger.
*   Use the CTRL-O key combination to save the file.
*   Use the CTRL-X key combination to exit the editor.
*   Restart the PHP service – stop and start with the following two commands:
    *   systemctl stop php7.4-fpm

    *   systemctl start php7.4-fpm


## Third Party Resources

From Key CDN: [Fixing 413 Request Entity Too Large Errors](https://web.archive.org/web/20240304153433/https://www.keycdn.com/support/413-request-entity-too-large)

- - -

### More Topics In Troubleshooting & Faqs

*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Common Server Deployment Issues & Error Messages](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/common-server-deployment-issues/)
*   [Server FAQs](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240304153433/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
