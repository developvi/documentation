---
title: "SSL Rate Limits"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: SSL Rate Limits
  parent: 13-Articales
  order: 12
---
When you enable SSL on a site, we use certificates issued by [LetsEncrypt](https://web.archive.org/web/20240529145328/https://letsencrypt.org/).

As with most web services, LetsEncrypt has rate limits to prevent abuse and DDOS attacks. You should be aware of these limits because they can affect whether or not you’re issued an SSL certificate for your new sites.

Notable limits are:

*   5 new certificates for the same domain every 7 days. This limit is the most common trap that trips admins up. If you continually try to issue an SSL certificate because you’re getting an error you will quickly run into this limit. Once you hit this limit you’ll have to wait 7 days to attempt to issue the certificate again.
*   There is a Failed Validation limit of 5 failures per account, per hostname, per hour. Continually attempting to issue an SSL certificate because you’re getting an error will quickly run you into this limit – if you encounter it you will have to wait 60 minutes before trying again.
*   There is a limit of 50 subdomain certificates every 7 days. So, if you have an top-level domain such as _mydomain.com_, you can only have 50 subdomain certificates of the format _subdomain.mydomain.com_ issued per week. If you’re selling site subscriptions you might hit this limit if you’re selling more than 50 subscriptions per week.

You can view all limits here: [LetsEncrypt Rate Limits](https://web.archive.org/web/20240529145328/https://letsencrypt.org/docs/rate-limits/)

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240529145328/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
