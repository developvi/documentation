---
title: "Understanding PHP Restrictions"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Understanding PHP Restrictions
  parent: 03-Adminstrator-guide
  order: 23
---
When we install a site, we assume that it is going to be run in a shared environment. This means that some important PHP restrictions are added.

First and foremost, we add the **open\_basedir** directive to ensure that PHP will only access the designated folders. These folders are the folders that WordPress is installed in and a TMP folder.

Next we disable a set of sensitive functions to prevent PHP from using them – we provide the list of disabled functions at the end of this document.

We also apply the following restrictions:

In version 3.0.0 and later we apply:

*   allow\_url\_fopen = 0
*   allow\_url\_include = 0
*   session.use\_strict\_mode = 1
*   session.cookie\_httponly = 1
*   session.use\_cookies = 1
*   session.use\_only\_cookies = 1
*   session.use\_trans\_sid = 0
*   session.name = <domain>
*   session.referer\_check = <domain>

In version 2.9.0 we applied:

*   allow\_url\_fopen = 0
*   allow\_url\_include = 0
*   session.use\_strict\_mode = 1
*   session.cookie\_httponly = 1
*   session.use\_cookies = 1
*   session.use\_only\_cookies = 1
*   session.use\_trans\_sid = 0
*   session.name = <domain>
*   session.referer\_check = <domain>

These restrictions are located in the _/etc/php/**7.4**/fpm/pool.d/**domain**.conf_ file on your server. The items in bold can change – 7.4 can be replaced with the version of php you’re running and domain is replaced with your domain name for the site.

Certain plugins or themes might need some of these restrictions lifted – to do so just edit the pool file for the domain and update them. Just be careful that you don’t inadvertently allow plugins and themes to access other sites if you’re in a shared environment.

#### Updraft Plus Plugin

The technical support folks at Updraft Plus states the the following restricted functions need to be enabled. Note that we have been able to use this plugin with these functions restricted but if you run into issues yourself you might need to remove these from your restricted list. If you do, you probably should not be running those sites in a shared environment!

*   shell\_exec
*   exec
*   system

## Appendix: List of disabled functions in PHP

In version 3.0.0 and later we disable:

*   dl
*   exec
*   fpassthru
*   getmypid
*   getmyuid
*   highlight\_file
*   ignore\_user\_abort
*   link
*   opcache\_get\_configuration
*   passthru
*   pcntl\_exec
*   pcntl\_get\_last\_error
*   pcntl\_setpriority
*   pcntl\_strerror
*   pcntl\_wifcontinued
*   phpinfo
*   popen
*   posix\_ctermid
*   posix\_getcwd
*   posix\_getegid
*   posix\_geteuid
*   posix\_getgid
*   posix\_getgrgid
*   posix\_getgrnam
*   posix\_getgroups
*   posix\_getlogin
*   posix\_getpgid
*   posix\_getpgrp
*   posix\_getpid
*   posix\_getppid
*   posix\_getpwnam
*   posix\_getpwuid
*   posix\_getrlimit
*   posix\_getsid
*   posix\_getuid
*   posix\_isatty
*   posix\_kill
*   posix\_mkfifo
*   posix\_setegid
*   posix\_seteuid
*   posix\_setgid
*   posix\_setpgid
*   posix\_setsid
*   posix\_setuid
*   posix\_times
*   posix\_ttyname
*   posix\_uname
*   proc\_close
*   proc\_get\_status
*   proc\_nice
*   proc\_open
*   proc\_terminate
*   shell\_exec
*   show\_source
*   source
*   system
*   virtual

In version 2.9.0 we disabled:

*   php\_uname
*   getmyuid
*   getmypid
*   passthru
*   leak
*   listen
*   diskfreespace
*   tmpfile
*   link
*   ignore\_user\_abort
*   shell\_exec
*   dl
*   set\_time\_limit
*   exec
*   system
*   highlight\_file
*   source
*   show\_source
*   fpassthru
*   virtual
*   posix\_ctermid
*   posix\_getcwd
*   posix\_getegid
*   posix\_geteuid
*   posix\_getgid
*   posix\_getgrgid
*   posix\_getgrnam
*   posix\_getgroups
*   posix\_getlogin
*   posix\_getpgid
*   posix\_getpgrp
*   posix\_getpid
*   posix
*   posix\_getppid
*   posix\_getpwnam
*   posix\_getpwuid
*   posix\_getrlimit
*   posix\_getsid
*   posix\_getuid
*   posix\_isatty
*   posix\_kill
*   posix\_mkfifo
*   posix\_setegid
*   posix\_seteuid
*   posix\_setgid
*   posix\_setpgid
*   posix\_setsid
*   posix\_setuid
*   posix\_times
*   posix\_ttyname
*   posix\_uname
*   proc\_open
*   proc\_close
*   proc\_get\_status
*   proc\_nice
*   proc\_terminate
*   phpinfo
