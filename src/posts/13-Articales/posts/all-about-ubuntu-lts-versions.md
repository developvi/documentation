---
title: "All About Ubuntu LTS Versions"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: All About Ubuntu LTS Versions
  parent: 13-Articales
  order: 15
---
DevelopVIDeploy builds all its servers on Ubuntu LTS operating systems (see [DevelopVIDeploy requirements](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)). Currently those would be Ubuntu 20.04 LTS and 22.04 LTS. As of [DevelopVIDeploy 5.3.8](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/recent-wpclouddeploy-maintenance-updates/), the default is 20.04 LTS.

In 5.3.9 the default will be Ubuntu 22.04 LTS.

But what does “Long Term Version” mean for Ubuntu?

The “LTS” suffix in the OS name actually means “Long Term Support” which is currently at least 5 years of free support. You have the option to purchase an additional 5 years of extended support for a total of 10 years of support!

In the world of operating systems, that’s HUGE.

But it gets better.

Each LTS version comes with its own repository of applications such as MariaDB and NGINX. The publishers of Ubuntu (Canonical) commit to keeping all those packages up to date with security fixes.

So, for example, all the packages that were included in the Ubuntu 18.04 LTS repository are still getting security updates which are available to customers who are willing to pay for them. This is despite the fact that the free support period is over. Paid support and security updates will be available until 2028!

Recently MariaDB announced that MariaDB 10.3 will no longer be supported with security fixes. And WordPress 6.3.1 started to flag any site running it as not being supported (in the health check screen).

But, if you’re running an Ubuntu LTS version (20.04 LTS and 22.04 LTS), urgent security fixes will be back-ported to MariaDB 10.3 and made available via the respective Ubuntu repositories!

The relevant commitment on the [Ubuntu LTS page](https://web.archive.org/web/20240304160814/https://ubuntu.com/blog/what-is-an-ubuntu-lts-release) states: “each flavour releases an LTS with the same Ubuntu release cadence, and flavours are **backed by the full Ubuntu archive for packages and updates**.”

The key in that statement is the package archive. That archive contains the most popular 3rd party packages and Canonical commits to keeping the updated even when the original publishers have officially ceased updates!

Additional commitment statements on are on the [Ubuntu Release Cycle](https://web.archive.org/web/20240304160814/https://ubuntu.com/about/release-cycle) page. And you can read all about security release on the [Security Team’s FAQ page](https://web.archive.org/web/20240304160814/https://wiki.ubuntu.com/SecurityTeam/FAQ).

## WordPress Health Check Database Warning

If you’re seeing a WordPress notice about MariaDB being outdated, you can rest easy – Canonical will keep you covered and make sure it gets appropriate security updates . Instead, you can take the time to create a solid plan to deploy new Ubuntu 22.04 LTS servers (which ships with MariaDB 10.06) and slowly push your sites over to it. Of course, the sooner you do this the better since, at the very least, you will benefit with the performance improvements included with MariaDB 10.6.

One of the criticisms about using the MariaDB versions in the Ubuntu repos is that they’re not the latest and greatest. But, our thoughts are that, unless you absolutely require the minute speed improvements in the latest releases, you’re better off with the additional security and integration work that Canonical does in order to offer a 10 year support cycle. Our default installations reflect this view.

(But, of course, if you really really want the latest and greatest MariaDB version (eg: 10.11 or 11.x), our services group would be happy to upgrade you for a nominal fee – but we do recommend that you have a really really good reason for doing so.)

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240304160814/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
