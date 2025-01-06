---
title: "How To Access The Entire Server via sFTP"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Access The Entire Server via sFTP
  parent: 08-tips-techniques-education
  order: 2
---
So, you want access to the entire server using sFTP? That’s easy – use the _root_ user and the _root_ or _sudo_ users’ private ssh key. It’s the same private key you used in the DVI settings screen.

For AWS, AZURE & ALIBABA , use the _ubuntu_ user and for GCP use the _wpcdadmin_ user instead of ‘root’. The private key for these users is also the one you used in the DVI settings screen.

There are a couple of alternatives:

1.  Setup a new SUDO user. You’ll need to do this from the command line. Depending on the provider you might be able to create one that only uses a password or you might need to generate an SSH key pair for them as well.
2.  Setup a password for your root user. Only certain providers will allow this but you can do this from the DVI dashboard – just go to the USERS tab for your server. [Learn more about this option in the documentation.](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/).

- - -

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [How To Generate an SSH Key Pair](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240420005500/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
