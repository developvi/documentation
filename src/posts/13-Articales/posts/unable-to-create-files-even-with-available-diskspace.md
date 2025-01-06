---
title: "Unable To Create Files (Even With Available Diskspace)"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Unable To Create Files (Even With Available Diskspace)
  parent: 13-Articales
  order: 13
---
Sometimes you might find yourself in the odd situation where Linux is reporting that you’re out of disk space. But when you examine the output of the **du -h** command it turns out that you have lots of space.

So what gives?

The answer is probably inodes.

_inodes are internal file system data structures that describe files and directories._

**The number of possible inodes is limited and set during partition creation. That means you can run out of them and be unable to create any new files, even if there is a lot of available space on the device.**

Normally this isn’t an issue. BUT, if a process ends up creating a lot of tiny files without deleting them then you’re likely to run out of inodes.

To find out if you’re out of inodes, run:

sudo df -i

The output will look something like this:

[![](https://web.archive.org/web/20240529142938im_/https://wpclouddeploy.com/wp-content/uploads/2023/06/Snag_955532fd.png)](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/wp-content/uploads/2023/06/Snag_955532fd.png)

The column **IUse** will contain the percent of inodes that have been used. Chances are that, if you’re reading this article, one of those entries will contain ‘100%’.

## Tracking Down The Errant Files

So how do you find out where these millions of tiny files are located?

In the case of WordPress and the world of webservers, the issue is likely to involve the OPENLITESPEED webserver and PHP.

In particular, the failure of LITESPEED/PHP to delete PHP session files.

Session files are located in the /**var/lib/lsphp/session/lsphp??** folders. eg: for php 8.1 they are located in the **/var/lib/lsphp/session/lsphp81 folder**.

To find out if there are a lot of files in these folders, navigate to /var/lib/lsphp/session/lsphp81:

cd /var/lib/lsphp/session/lsphp81

Then run the following command:

sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n

The output will include the number of files below each php folder.

[![](https://web.archive.org/web/20240529142938im_/https://wpclouddeploy.com/wp-content/uploads/2023/06/wpcd-diskspace-inodes-02.png)](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/wp-content/uploads/2023/06/wpcd-diskspace-inodes-02.png)

In the example above, you can see that the lsphp81 folder has over 15 million files!

If you were to navigate into it and list out the files you will see that the files all start with ‘sess\_’.

You might think that the obvious solution would be to try a command such as _rm sess\_\*_. Except that will not work – you’ll end up with an error along the lines of

bash: /usr/bin/rm: Argument list too long

This is because Linux/bash is expanding the asterisk into individual file names before processing the command. (It’s just how the bash interpreter is designed to work).

Instead, you have to navigate into the problematic folder and then use the following command:

sudo find . -name "sess\_\*" -delete

With millions of files, it will likely take a long time to run. And you’ll probably need to repeat it for all the other PHP version folders.

Once you’ve finished cleaning up, running _df -i_ again should show a low percent usage of inodes.

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Managing Linux Updates](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240529142938/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
