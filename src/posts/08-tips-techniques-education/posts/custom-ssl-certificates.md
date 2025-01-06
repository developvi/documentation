---
title: "Custom SSL Certificates"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Custom SSL Certificates
  parent: 08-tips-techniques-education
  order: 22
---
DevelopVIDeploy does not officially support custom SSL certificates.

However, that does not mean you cannot add one to your site.

A typical use-case would be that you’ve accidentally exceeded the attempts to get a certificate from LetsEncrypt (the default on our SSL tab). Instead of waiting seven days to retry while your site remains without SSL, you might choose to install a custom certificate.

You can find suppliers of SSL certificates for under $10.00. For example https://cheapsslsecurity.com.

However, beware that upon checkout, many suppliers will set your period to 5 years or more. So your $10.00 certificate is suddenly $50.00. Since the use of a custom SSL certificate tends to be temporary, you really want to make sure you’re only paying for one year.

Typically, you first purchase a certificate and then you go through a workflow after checkout where you can use the certificate by specifying and validating your domain.

Most of these suppliers will then send you files specific to your web server. For example, you can specify that your webserver is NGINX and they’ll send you generic files as well as a single PEM file suitable for NGINX which will include all the intermediate certificates.

The provider of the certificate will typically have instructions for how to install the certificate on an NGINX server.

For DevelopVIDeploy, the general flow is something like this:

*   Login to your server with SSH
*   Upload the PEM and KEY files to the _/etc/ssl_ folder
*   Open the vhost file located at _/etc/nginx/sites-enabled/yourdomain.com:_ **\[**_sudo nano /etc/nginx/sites-enabled/yourdomain.com_**\]**
*   Remove the two **listen 80** lines close to the top of the file (around line 9)
*   At the bottom of the file before the close “}”, add in the following lines (replacing the filename.pem and filename.key portion with the files you received from your SSL vendor.

\# custom ssl cert.
listen 443;
ssl on;
ssl\_certificate /etc/ssl/filename.pem;
ssl\_certificate\_key /etc/ssl/filename.key;

*   At the very bottom of the file (after the closing “}”) you would add something like this to redirect HTTP requests to HTTPS requests:

server {
if ($host = www.yourdomain.com.com) {
return 301 https://$host$request\_uri;
}

if ($host = yourdomain..com) {
return 301 https://$host$request\_uri;
}

listen 80;
listen \[::\]:80;

server\_name yourdomain.com www.yourdomain.com;
return 404;
}

*   Save and close the file: _ctrl-o <enter>_ and _ctrl-x_ will save the file and exit you from the nano editor
*   Restart the NGINX server: _sudo systemctl restart nginx_

There are going to be nuances depending on your SSL vendor and other factors such as security (eg: you might want to restrict the TLS protocols and CIPHERS used).

But the basic idea is that:

*   You get two SSL related files (PEM and KEY) from your SSL vendor (technically you provide the KEY file but usually they help you generate it as part of the SSL provisioning workflow after your purchase.)
*   You upload these files to the _/ssl_ folder on your server.
*   Then you tell NGINX about the files and redirect all port 80 HTTP requests to port 443 HTTPS.

- - -

## Next Steps

Now we should let DVI know that a custom SSL certificate is installed. This will allow certain generated links to automatically use https:// instead of just http://.

*   Navigate to **WpCloudDeploy** → **ALL APPS** (or **WpCloudDeploy** → **ALL WORDPRESS SITES**)
*   Scroll down to the site where you just installed your custom SSL certificate and click on the title – this will bring up the site details screen
*   Click on the **SSL** tab
*   Click on the **FLIP CUSTOM SSL STATUS FLAG** button inside the card with the same title.

- - -

## Caution

Please do not attempt to do anything involving SSL inside DVI until you remove your file edits. Otherwise, you might corrupt the configuration files and the web server will refuse to start!

We recommend that you add an APP GROUP as well as a LABEL to the site so that it’s obvious in your site list that the site is using a custom SSL certificate.

We have tested the most common operations with custom SSL certificates and they seem to work just fine. But because this involves customizations to our existing stack, free support is not available if something funky occurs.

If you have more than one site with custom SSL certificates you might want to consider placing them on their own VM.

- - -

## Possible Additional Directives

The above are the minimum NGINX directives required to get SSL working. However, you might want to add in the following just below the _ssl\_certificate\_key_ directive.

ssl\_session\_cache shared:le\_nginx\_SSL:10m;
ssl\_session\_timeout 1440m;
ssl\_session\_tickets off;

ssl\_protocols TLSv1.2 TLSv1.3;
ssl\_prefer\_server\_ciphers off;

ssl\_ciphers "ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384";

Generally, these turn off insecure protocols.

- - -

## Wrapup

By owning and managing your own servers, you’re able to things that are outside the feature scope of ‘standard’ software or SaaS services. This is an example of something that you can do even though it’s not officially supported inside DevelopVIDeploy.

- - -

### More Topics In Command Line

*   [Advanced Backups](https://web.archive.org/web/20240419234849/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240419234849/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [Alias Domains](https://web.archive.org/web/20240419234849/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [How To Login To Your Server Via SSH](https://web.archive.org/web/20240419234849/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)
*   [Server Configuration Files](https://web.archive.org/web/20240419234849/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-configuration-files/)
