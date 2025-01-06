---
title: "Managing SSL Certificates"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Managing SSL Certificates
  parent: 02-User-guide
  order: 6
---
Most of the websites you deploy will require an SSL certificate. In DevelopVIDeploy, your certificate can be automatically issued by [LetsEncrypt](https://web.archive.org/web/20240420014806/https://letsencrypt.org/).

Before you can request and install a certificate, you must make sure that your DNS (Domain Name Service) is configured to send visitors to the server where the website is installed.

When you have configured your DNS you can install your certificate as follows:

*  Go to **DevelopVIDeploy** → **Applications**
*  Click on the site for which you need an SSL certificate
*  Click on the **SSL** tab
*  Click on the **SSL Status** toggle switch and then click the **OK** button on the confirmation message

If all goes well, the screen will refresh itself after about a minute or so and the toggle switch should now be blue instead of gray.

If something goes wrong you will see a popup message to that effect.

You can view a full log of the server actions by navigating to **DevelopVIDeploy** → **SSH Logs**. This will be particularly useful if the attempt to secure a certificate fails.

## Remove A Certificate

If you ever need to remove a certificate:

*  Go to **DevelopVIDeploy** → **Applications**
*  Click on the site for which you need an SSL certificate
*  Click on the **SSL** tab
*  Click on the **SSL Status** toggle switch and then click the **OK** button on the confirmation message

## Using Proxy Services

_If you’re having issues with creating SSL certificates, we recommend that you turn off any proxy service such as CloudFlare and try again. This is especially true if you have page rules that might redirect to another page or firewall rules that might prevent certain types of traffic._

## CloudFlare

Are you using CloudFlare? If so, please review some of our CloudFlare notes if you’re running into issues:

*  [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)

## Notes

*  We attempt to request two certificates – one for _www.yourdomain.com_ and one for just _yourdomain.com_. For a top-level domain, this should succeed for both requests. If you’re requesting a certificate for a subdomain, only the second request will succeed. As long as one of the requests succeeds and a certificate is acquired the operation will be considered a success.
*  [LetsEncrypt has a limit to the number of times you can request a certificate for a single domain](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/). After that limit has been exceeded every request for that domain will fail until the timeout period has passed. As of the date we updated this article, you have up to FIVE failed attempts per domain per hour (this may change in the future). So, if you have tried more than twice to obtain an SSL certificate and both those attempts failed you might want to contact our support team before making any more attempts. You can learn all the LetsEncrypt limits [here](https://web.archive.org/web/20240420014806/https://letsencrypt.org/docs/rate-limits/).
*  Another LetsEncrypt limit to be aware of is the DUPLICATE CERTIFICATES limit. You can only request a certificate for the same domain FIVE times within a one week period. So if you’re doing a lot activations for the same domain because you’re testing stuff, that domain can be locked out for 7 days if you’re not aware of this limit.
*  If, for some reason, you have exceeded the LetsEncrypt limit requests for your domain and you have your domain name server on CloudFlare, you can try to use CloudFlare’s SSL options to temporarily provide a certificate for your site. Once the LetsEncrypt timeout period has expired you can remove the temporary CloudFlare SSL and retry your SSL request.

## Custom Certificates

[View the Custom Certificates article](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/).

### More Topics In User Guide

*  [A Quick Tour](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/a-quick-tour/)
*  [Deploy A Server](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/deploy-a-server/)
*  [Deploy A New WordPress Site](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/add-a-new-wordpress-site/)
*  [Delete A Server](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-server/)
*  [Delete A Site](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/delete-a-site/)
*  [Page Cache](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/page-cache/)
*  [Managing sFTP Users](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/managing-sftp-users/)
*  [Cloning (Copying) Sites](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/cloning-sites/)
*  [Webservers: NGINX & OpenLiteSpeed](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/webservers-nginx-openlitespeed/)
*  [Copy Site To Another Server](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-another-server/)
*  [Copy Site To/Over Another Site](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/copy-site-to-over-another-site/)
*  [Staging Sites](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/staging-sites/)
*  [Changing A Domain](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/changing-a-domain/)
*  [Notes for cloning sites, changing servers & changing domains](https://web.archive.org/web/20240420014806/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/considerations-and-gotchas-when-cloning-sites-changing-servers-and-or-changing-domains/)
