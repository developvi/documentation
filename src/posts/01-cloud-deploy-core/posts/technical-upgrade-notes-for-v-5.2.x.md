---
title: "Technical Upgrade Notes For V 5.2.x"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Technical Upgrade Notes For V 5.2.x
  parent: 01-cloud-deploy-core
  order: 13
---
## Introduction

In version 5.2.0 of DVI we’ve changed a few things that require some manual updates to servers and sites created with prior versions of version 5.x. In particular:

*   We’ve changed the way certain security options are implemented in OLS to work around OLS bugs
*   We’ve tweaked our backup scripts to fix a couple of bugs introduced by the new remote database option

Unfortunately you need to make these changes manually using the command line.

_Note: If you’re upgrading from 4.16 or 4.17 and have never installed 5.x, you should follow the [5.x upgrade instructions](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/) instead. Nothing in this 5.2 upgrade document will apply in this case._

- - -

## Changes for All Servers

### Reset Your Backups

We have updated our backup scripts. If you’re using our backups, you should disable and re-enable them.

Just a reminder that there are two places you can apply backups:

*   Servers: Automatically backs up all sites on the server
*   Sites: Backs up only the specified site

Please make sure you deactivate and reactivate in the places you are using them.

- - -

## Changes for OpenLiteSpeed Sites and Servers

**If you’re using OpenLiteSpeed** servers and sites created with versions earlier than DVI 5.2, then you will want to apply the following changes to each OLS server or site on the server. (No changes are required for NGINX servers.)

Please note that all the following needs to be done under your root/sudo login. This way all new files and folders created will be owned by the root user.

### 1\. Update global PHP.INI file for all PHP versions

Open the PHP 8.1 global ini file using your favorite editor – the command for the NANO editor is:

sudo nano /usr/local/lsws/lsphp81/etc/php/8.1/litespeed/php.ini

Search for _disable\_functions_

Replace that entire line with:

disable\_functions = pcntl\_alarm,pcntl\_fork,pcntl\_waitpid,pcntl\_wait,pcntl\_wifexited,pcntl\_wifstopped,pcntl\_wifsignaled,pcntl\_wifcontinued,pcntl\_wexitstatus,pcntl\_wtermsig,pcntl\_wstopsig,pcntl\_signal,pcntl\_signal\_get\_handler,pcntl\_signal\_dispatch,pcntl\_get\_last\_error,pcntl\_strerror,pcntl\_sigprocmask,pcntl\_sigwaitinfo,pcntl\_sigtimedwait,pcntl\_exec,pcntl\_getpriority,pcntl\_setpriority,pcntl\_async\_signals,pcntl\_unshare,

Repeat for each of the following files:

*   /usr/local/lsws/lsphp80/etc/php/8.0/litespeed/php.ini
*   /usr/local/lsws/lsphp74/etc/php/7.4/litespeed/php.ini

If you’re on Ubuntu 20.04, also repeat for the following files:

*   /usr/local/lsws/lsphp73/etc/php/7.3/litespeed/php.ini
*   /usr/local/lsws/lsphp72/etc/php/7.2/litespeed/php.ini
*   /usr/local/lsws/lsphp71/etc/php/7.1/litespeed/php.ini

- - -

### 2\. Modify the vhconf.conf File for Each Site

Open your vhconf.conf file for one of your sites on your OLS server using your favorite editor – the command for the NANO editor is:

nano /usr/local/lsws/conf/vhosts/**YOURDOMAIN.COM**/vhconf.conf

Search for the keyword **PHP\_INI\_SCAN\_DIR**.

Replace everything on the line where that was found with this:

env PHP\_INI\_SCAN\_DIR=:$VH\_ROOT/.phpini

Repeat for all your OLS sites.

- - -

### 3\. Create a PHP.INI file for Each Site

Run the following command, replacing YOURDOMAIN.COM with your real domain:

mkdir /var/www/**YOURDOMAIN.COM**/.phpini

Then run the following to create the php.ini file and add contents:

nano /var/www/**YOURDOMAIN.COM**/.phpini/php.ini

This file should contain the following line:

disable\_functions = dl, exec, fpassthru, getmypid, getmyuid, highlight\_file, link, opcache\_get\_configuration, passthru, pcntl\_exec, pcntl\_get\_last\_error, pcntl\_setpriority, pcntl\_strerror, pcntl\_wifcontinued, phpinfo, popen, posix\_ctermid, posix\_getcwd, posix\_getegid, posix\_geteuid, posix\_getgid, posix\_getgrgid, posix\_getgrnam, posix\_getgroups, posix\_getlogin, posix\_getpgid, posix\_getpgrp, posix\_getpid, posix\_getppid, posix\_getpwnam, posix\_getpwuid, posix\_getrlimit, posix\_getsid, posix\_getuid, posix\_isatty, posix\_kill, posix\_mkfifo, posix\_setegid, posix\_seteuid, posix\_setgid, posix\_setpgid, posix\_setsid, posix\_setuid, posix\_times, posix\_ttyname, posix\_uname, proc\_close, proc\_get\_status, proc\_nice, proc\_open, proc\_terminate, shell\_exec, show\_source, source, system, virtual

Repeat for all your OLS sites

- - -

### 4\. Restart your OLS server

Once all the changes in sections 1 – 3 above have been made, you need to restart your server so that the changes can take effect:

*   Navigate to the **SERVICES** tab for your OLS server
*   Under the **CORE SERVICES STATUS** section, click the **RESTART** button next to the _OpenLiteSpeed Web Server_ label.

- - -

## A Deep Dive Explanation of Of The OLS Changes

- - -

_(And an example of why OLS is still categorized as beta in 5.x)._

If you’re really curious, you might be wondering about why the OLS changes described above are necessary.

In short, the _phpIniOverride_ sections of a site’s _vhconf.conf_ file did not respect ALL php directives.

Each site is given its own _vhconf.conf_ file that contains everything needed to configure a site for use in OpenLiteSpeed. Inside this file are multiple sections where we can specify php.ini directives. In theory, directives in these _phpIniOverride_ sections should apply to the site.

Unfortunately, this is not always the case and many important security related directives were just being ignored by OLS and its PHP handler.

After many frustrating communication rounds with OLS reps, it became obvious that they did not see this as an issue (or decided to hide it). Regardless, we had to adopt a new approach.

The new approach is to place the directives in a php.ini file associated with the site. But we need to do this in a way that a regular sFTP user cannot edit (otherwise they can simply remove the security directives).

So, a site’s php.ini file is now placed in a new folder /var/www/YOURDOMAIN.COM/.phpini and is owned by root. Only root/sudo users can change this file.

- - -

### More Topics In DevelopVIDeploy Core

*   [Introduction, Installation & Quick Start Guide](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/introduction-to-wpcloud-deploy/)
*   [Requirements](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/)
*   [Quick Start](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start/)
*   [Quick Start With The DVI Wizard](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-wizard/)
*   [Quick Start With DigitalOcean Image](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/quick-start-with-digitalocean-image/)
*   [Quick Start With AWS Image](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-with-aws-image/)
*   [Generic Quick Start Guide](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-user-guide/quick-start-the-harder-way/)
*   [Release Notes](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/release-notes/)
*   [Technical Upgrade Notes For V 4.3.0](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-2-5/)
*   [Technical Upgrade Notes For V 4.6.x](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-4-6-0/)
*   [Technical Upgrade Notes For V 5.0.x](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-0-x/)
*   [Technical Upgrade Notes For V 5.3.0](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-3-0/)
*   [Technical Upgrade Notes For V 5.7.0](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/technical-upgrade-notes-for-v-5-7-0/)
*   [PHP 8.0, 8.1, 8.2 & 8.3 Notes](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/php-8-0-8-1-notes/)
*   [PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/more/php-5-6-7-0-7-1-7-2-7-3-notes/)
*   [HTTP/2](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/http-2/)
*   [Root User Passwords](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/root-user-passwords/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Free Setup Requirements & Checklist](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/free-setup-requirements-checklist/)
*   [Better DVI Crons](https://web.archive.org/web/20240420011837/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/)
