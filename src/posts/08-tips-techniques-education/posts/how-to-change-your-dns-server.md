---
title: "How To Change Your DNS Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Change Your DNS Server
  parent: 08-tips-techniques-education
  order: 12
---
## Introduction

When we deploy a server, we use the default DNS setup by the server provider. For example, in the case of VULTR, their DNS server might be something like 127.0.0.53.

However, you might want to use a different DNS resolver – either for privacy, speed, redundancy or because the default DNS server is having issues.

## How To Do It

The data for the DNS resolver is in the _/etc/resolv.conf_ file.

Open the file in the NANO editor:

sudo nano /etc/resolv.conf

Somewhere in that file you should see at least one line that starts with the term _nameserver_ followed by an ip address:

[![](https://web.archive.org/web/20240304140727im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-01.png)](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-01.png)

Just before that line, add your own resolver. For example:

[![](https://web.archive.org/web/20240304140727im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-02.png)](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-02.png)

You can add as many resolvers as you like. They will be evaluated in the order listed. For example:

[![](https://web.archive.org/web/20240304140727im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-03.png)](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/wp-content/uploads/2022/12/wpcd-how-to-change-dns-servers-03.png)

When you ready to save the file:

ctrl-o

Enter

Exit:

ctrl-x

The settings take effect immediately and there should be no need to restart the server.

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240304140727/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
