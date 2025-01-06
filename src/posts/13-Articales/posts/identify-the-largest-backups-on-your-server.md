---
title: "Identify The Largest Backups On Your Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Identify The Largest Backups On Your Server
  parent: 13-Articales
  order: 11
---
As you are probably aware, DVI allows you to keep some backups locally on your server. This makes it a snap to restore to a known checkpoint.

However, those backups take disk space. And, sometimes you might want to know which site backups are using the most space.

Here is how you can get this information:

## Step 1: SSH Into Your Server

You need to run the linux _du_ command directly on the server which means SSH.

So, login to your server as root/sudo via ssh.

[Learn more about ssh logins for DevelopVIDeploy servers](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)

## Step 2: Navigate To The DVI Backups Folder

cd ~/wp-backup

If you get an error try one of the following instead:

cd /root/wp-backup

or

sudo cd /root/wp-backup

## Step 3: Run This DU Command

sudo du -sh \*

The output should look something like this:

1.7G domain1.com
8.8G domain2.com
3.6G domain3.com
129M domain4.com
21G  domain5.com
5.0G domain6.net
18G  domain7.com
5.9G domain8.com

The first column contains the size of the folder – in the above example _domain1.com_ is using 1.7 gigabytes of backup space and _domain2.com_ is using 8.8 gigabytes \[of backup space\]. _Domain4.com_ is only using 129 megabytes.

You’ll notice that the output isn’t sorted by size. To get a sorted output, use this instead:

sudo du -sh \* | sort -h

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240420011427/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
