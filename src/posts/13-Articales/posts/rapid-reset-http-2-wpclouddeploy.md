---
title: "Rapid Reset HTTP/2 & DevelopVIDeploy"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Rapid Reset HTTP/2 & DevelopVIDeploy
  parent: 13-Articales
  order: 16
---
On October 10th 2023, information about an [HTTP/2 vulnerability (CVE-2023-44487)](https://web.archive.org/web/20240304160449/https://www.cve.org/CVERecord?id=CVE-2023-44487) that could cause a Denial of Service (DDOS) attack on sites was released. It now goes by the name “Rapid Reset HTTP/2”.

If you are concerned about being a victim of this type of attack, there are things you can do to help mitigate it.

First, you can place your servers and sites behind a proxy such as CloudFlare. The services have already rolled out mitigations against these kinds of attacks and will drop the traffic before it even hits your servers.

AWS, Google Cloud and Microsoft Azure already have mitigations in place to address the threat so if your servers are running there you are also benefiting from the protections they have put in place to address the issue. It is possible other Cloud Server Providers have also rolled out protections as well.

Second, if you are running NGINX, you can apply their recommended changes to your servers – you can view those recommendations on the related [NGINX blog article](https://web.archive.org/web/20240304160449/https://www.nginx.com/blog/http-2-rapid-reset-attack-impacting-f5-nginx-products/).

In particular, they are recommending the following:

*   **keepalive\_requests** should be kept at the default of 1000. For DVI, our default stack does not modify this value so it should already be using the 1000 default value. This configuration item is set in /etc/nginx/nginx.conf. See the [NGINX docs on keepalive\_requests](https://web.archive.org/web/20240304160449/http://nginx.org/en/docs/http/ngx_http_core_module.html#keepalive_requests) more more information.
*   **http2\_max\_concurrent\_streams** should be kept at the default of 128 streams. DVI’s default stack does not modify this value either so you should not have to make any changes to it. View the [NGINX docs on http2\_max\_concurrent\_streams.](https://web.archive.org/web/20240304160449/http://nginx.org/en/docs/http/ngx_http_v2_module.html#http2_max_concurrent_streams) DVI’s default stack does not turn on HTTP/2 on NGINX so if you haven’t flipped the flag for a site, then this is probably a non-issue for it.

They are also recommending that you look at the following two directives:

*   **limit\_conn** which enforces a limit on the number of connections allowed from a single client. DVI’s default stack does not modify this value. [Read more about _limit\_conn_ in the NGINX documentation](https://web.archive.org/web/20240304160449/https://nginx.org/en/docs/http/ngx_http_limit_conn_module.html).
*   **limit\_req** which enforces a limit on the number of requests that will be processed within a given amount of time from a single client. This one is trickier because it depends on the site/application and how it’s used. **The DVI default stack does set a limit on the number of requests that can hit the wp\_login page**. Otherwise, any other pages are set to the NGINX default. You can [read more about limit\_req in the NGINX docs](https://web.archive.org/web/20240304160449/https://nginx.org/en/docs/http/ngx_http_limit_req_module.html).

The bottom line is that, for DVI, you shouldn’t have to make any changes to your NGINX configuration if you’re using our default stack and values.

## OpenLiteSpeed

The OpenLiteSpeed folks are stating that they are NOT affected by this vulnerability because of the way they’ve developed their implementation of HTTP/2. So, again, for DVI, you should not have to make any changes if you’re using our default configuration.

You can read [more about OpenLiteSpeed’s analysis of the issue](https://web.archive.org/web/20240304160449/https://blog.litespeedtech.com/2023/10/11/rapid-reset-http-2-vulnerablilty/) on their site.

## Additional Resources

if you are running other application stacks besides DVI, you should [check out this github repository where recommendations are being updated for multiple stacks that are affected](https://web.archive.org/web/20240304160449/https://gist.github.com/adulau/7c2bfb8e9cdbe4b35a5e131c66a0c088).

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240304160449/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
