---
title: "Identify The Largest Files In The WordPress Uploads Folder"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Identify The Largest Files In The WordPress Uploads Folder
  parent: 13-Articales
  order: 9
---
The uploads folder in your average WordPress site can contain a ton of random files, some of them very large. Here’s a quick way to identify the top 10 largest files in there:

## Step 1: SSH Into Your Server

You need to run the linux _find_ command directly on the server which means SSH.

So, login to your server as root/sudo via ssh.

[Learn more about ssh logins for DevelopVIDeploy servers](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)

## Step 2: Run This Find Command

sudo find /var/www/**<yourdomain.com>**/html/wp-content/uploads/ -printf '%s %p\\n'| sort -nr | head -10

Replace the <yourdomain.com> part of the path with your domain name.

The output should be the top 10 largest files in the WordPress uploads folder. Here’s an example of the output:

45076199 /var/www/yourdomain.com/html/wp-content//uploads/2022/01/Header-Photo-with-Texture.psd
25592723 /var/www/yourdomain.com/html/wp-content//uploads/2021/06/WebFrontPage\_V4.mp4
23879041 /var/www/yourdomain.com/html/wp-content//uploads/2021/06/Village-copy.jpg
20528424 /var/www/yourdomain.com/html/wp-content//uploads/2021/06/Vertical-Header-Short.mp4
15114449 /var/www/yourdomain.com/html/wp-content//uploads/2021/06/Updated-June-2021-v1-(1).mp4
14898841 /var/www/yourdomain.com/html/wp-content//uploads/2021/08/51375928663\_3ac41fd3d7\_o.png
14143500 /var/www/yourdomain.com/html/wp-content//uploads/2022/02/51893222623\_3de9eb3a58\_o.jpg
10396860 /var/www/yourdomain.com/html/wp-content//uploads/2016/11/Eventbrite\_Header.png
10342445 /var/www/yourdomain.com/html/wp-content//uploads/2022/02/Concourse-Photo.jpg
7903593 /var/www/yourdomain.com/html/wp-content//uploads/2021/06/50996962137\_8ecbcebbd7\_o.jpg

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240304155833/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
