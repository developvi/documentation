---
title: "Root User Passwords"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Root User Passwords
  parent: 03-Adminstrator-guide
  order: 31
---
You can set or change your root user password under the USERS tab for a server. However, before you do that, there are some things to note about passwords and root users:

1.  Some server providers do not allow SSH logins for root users with just a password.
2.  Some server providers DO allow SSH logins for root users with just a password. We do not change this setting when creating the server. If you do not want to allow your root admins to login with a password, you can change it yourself by editing the **etc/ssh/sshd\_config** file or by using the point-and-click interface we provide (instructions at the bottom of this document).
3.  DVI does not login to your server with a password – it uses SSH public-private key-pairs. So the absence or presence of a password for the root user does not make a difference in the day-to-day operations of the dashboard.
4.  If you lock yourself out of your server (eg: by using fail2ban or other firewalls without whitelisting your IP address), the only way back in might be using a root user password and the basic console from your server providers’ dashboard. So, if you’re messing around with firewalls, fail2ban or similar utilities, we recommend that you generate a password for your root user and enable ssh/sshd password authentication for the root/sudo user.

\*\*\*For most server providers, if you do not set a password for your root user and you are locked out, you will NOT be able to regain access to your server and there is nothing we can do about it!\*\*\*

Below is some information about the default configuration for server providers.

- - -

### The following server providers do not allow SSH logins for root users with just passwords:

*   DigitalOcean
*   Exoscale
*   Upcloud (servers provisioned after August 2021)

These providers have effectively set the _PermitRootLogin_ config option in **etc/ssh/sshd\_config** to _prohibit-password_.

You should consider overriding this option and setting a password for these servers. This will allow you to recover if you lock yourself out of the server and need to use the providers’ recovery console.

If you do override this option and set a password for root consider installing the fail2ban utility to throttle the bots that will be attempting to log into your server.

### The following server providers do allow SSH logins for root users with passwords:

*   Linode
*   Vultr
*   Upcloud (servers provisioned before August 2021)
*   Hetzner

If you do not want to allow root logins with passwords, you should disable the the _root password authentication_ capability for servers from these providers.

If you leave it enabled then consider installing the fail2ban utility on them.

- - -

### The following server providers will allow you a direct SSH or Serial connection from their dashboard without needing a password or key-pair:

*   Azure
*   AWS EC2
*   AWS Lightsail
*   Google

This means that if you ever lock yourself out of your server you will always have a way to get back in – if you can login to the providers’ dashboard.

- - -

### The following providers do not allow logins for root users with passwords at all – not from a console and not via SSH.

*   Alibaba

Try not to lock yourself out of these servers because you have no options to get back into them!

- - -

## Enabling or Disabling Password Authentication

You can disable password authentication on SSH logins for the root or primary SUDO user. To do this:

*   Go to DevelopVIDeploy->Cloud Servers and click on the server for which this action will apply
*   Click on the USERS tab
*   Click on either the ENABLE PASSWORD AUTHENTICATION or DISABLE PASSWORD AUTHENTICATION button.

[![](https://web.archive.org/web/20240529155842im_/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-084.png)](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/wp-content/uploads/2021/02/wpcd-v4-084.png)

As mentioned earlier in this document, certain server providers already disable SSH password authentication for the root user.

## Security Implications

The most secure configuration for your server is to completely disable passwords for root users and use ssh keys for root/sudo logins.

But, we know that s\*it happens. And since many of our customers are new to managing servers we do want to provide some options for recovering when bad stuff accidentally happens.

- - -

## Availability

Changing root user passwords from the UI is available in DVI V 4.6.0 or later. For prior versions you must log in via ssh and change it from the command line.

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.2.x](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-2-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Change Domain on Control Plane Server](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/change-domain-on-control-plane-server/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240529155842/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
