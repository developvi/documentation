---
title: "How To Lock A Linux User"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Lock A Linux User
  parent: 13-Articales
  order: 14
---
The Ubuntu flavor of Linux usually ships with a user called ‘ubuntu’. This is in addition to the ‘root’ user.

Cloud server providers such as DigitalOcean, Linode and Vultr default to the ‘root’ user. Other server providers default to the ‘ubuntu’ user.

If you’re using a cloud server provider that defaults to ‘root’, you can disable the ‘ubuntu’ user login without removing them from the server. This can be done with a simple command entered on the command line:

sudo passwd -l ubuntu

This will prevent the user from being able to login with a password. If the ‘ubuntu’ user does not exist then you’ll receive a simple error message such as _‘passwd: user ‘ubuntu’ does not exist’_

To lock any other user, just enter the user name in place of ‘ubuntu’ – i.e.:

sudo passwd -l _<username>_

Note that locking a user with this method does NOT prevent the user from being able to login if they have been configured for passwordless logins (eg: with ssh key-pairs). It only prevents them from using a password to login. If you’d like to prevent those types of logins as well you can use the _chage_ command to expire the user (see more information at the bottom of this article).

- - -

You can check the status of a user to see if they’re locked:

sudo passwd -S ubuntu

The output might look something like this:

ubuntu L 09/14/2023 0 99999 7 -1

If the second column in the output contains “L”, then the user is locked. In the above example output, the ‘ubuntu’ user is indeed locked.

You can check the status for ALL your users by using the following command:

sudo passwd -S --all

The output will look similar to this:

root P 07/04/2023 0 99999 7 -1
syslog L 02/17/2023 0 99999 7 -1
uuidd L 02/17/2023 0 99999 7 -1
tcpdump L 02/17/2023 0 99999 7 -1
tss L 02/17/2023 0 99999 7 -1
landscape L 02/17/2023 0 99999 7 -1
fwupd-refresh L 02/17/2023 0 99999 7 -1
usbmux L 06/16/2023 0 99999 7 -1
ubuntu L 09/14/2023 0 99999 7 -1

Notice that the second column in the output contains “L” indicating that the users are locked.

Learn more about the _passwd_ command on the [passwd page on the Ubuntu documentation site](https://web.archive.org/web/20240419235335/https://manpages.ubuntu.com/manpages/trusty/en/man1/passwd.1.html).

- - -

## Expiring A User Account

As mentioned earlier, locking a user does not prevent them from being able to login with certificates. To prevent this type of login, you must expire the user. eg:

chage -E0 ubuntu

Expiring an account uses the 8th field in /etc/shadow (using “chage -E”) – this will block all access methods that use PAM to authenticate a user.

To verify the account has expired, use:

chage -l ubuntu

The output should include a row that shows the expiration date:

Last password change : Apr 17, 2021
Password expires : never
Password inactive : never
Account expires : Jan 21, 1990
Minimum number of days between password change : 0
Maximum number of days between password change : 999999
Number of days of warning before password expires : 7

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240419235335/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
