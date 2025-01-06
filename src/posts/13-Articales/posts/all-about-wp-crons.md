---
title: "All About WP Crons"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: All About WP Crons
  parent: 13-Articales
  order: 7
---
## Introduction

The WP CRON process is an integral component of WordPress and is required to keep WordPress healthy. Straight out of the box it sets up 11 jobs (as of WP 6.0) that must each be run on a regular basis. Some need to run every hour and others can be run once a week.

[![](https://web.archive.org/web/20240529143433im_/https://wpclouddeploy.com/wp-content/uploads/2022/06/wp-cron-processes-01.png)](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/wp-content/uploads/2022/06/wp-cron-processes-01.png)

## How Does A Cron Process Get Triggered?

By default, every time WordPress receives a request it will first check to see if it’s time to run any jobs. If it is, it will run them. As you might expect, on a heavy site, this check incurs a performance penalty. And, in the event that a job needs to be run, the user will need to wait for that to run before the request can be completed.

Another issue can occur if a site isn’t accessed very often – scheduled jobs might never be run or might run late.

There is a solution to both of these issues though.

You can disable the normal ‘check on every request’ function with a WP-CONFIG.php flag (DISABLE\_WP\_CRON). Then, you can schedule the check to be done using a LINUX cron to call the WordPress cron-check directly. This means you can schedule the check to run once every 15 minutes or once every hour instead of on every request.

As you might expect, with DevelopVIDeploy [it is easy to make this switch for each site](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/).

## Cron Conflicts – A Deeper Dive Into How WP Cron Works

What happens if you set a cron schedule to run every minute and a job fails to complete in that time? Does a new job get started?

The answer to this actually depend on how WP CRON was invoked.

If you execute it with an HTTP request with ‘doing\_wp\_cron’ in the GET string, it will check if another wp-cron process has set a lock and exit if it has. By default, this is how WordPress executes it when checking on every request.

It is easily done this way using a Linux cron as well. In crontab you can enter something like this:

```javascript
*/10 * * * * /usr/bin/wget -q -O "http://www.example.com/wp-cron.php?doing_wp_cron=`date +\%s.\%N`" > /dev/null 2>&1
```

## Using PHP CLI

You can also call the WP CRON check process directly from the command line using PHP CLI.

In this case, things get a little bit more funky.

WordPress will check the WP\_CRON\_LOCK\_TIMEOUT constant which defaults to sixty seconds. **If the existing process has been running for longer than that, it claims the lock for its own and proceeds to run scheduled jobs starting all over at the beginning.**

You should read that bolded part again because it has some ramifications. Though, most of the time it is not as huge an issue as you might think.

WP-CRON **reschedules and un-schedules jobs as it goes.** Right before it runs a job, it un-schedules it. This usually prevents the job from running twice. And right after it finishes executing a job, it checks to make sure it still owns the lock. If it does not, it exits. If it still holds the lock, it will re-schedule the job that was just finished so it can run again at its future scheduled time.

That sounds good, right?

### Here’s where an issue can occur:

Lets assume you have some jobs that take twenty minutes to run and others that take 5 minutes to run. You start WP-CRON from the command line and it chugs away at the 20 minute job for a bit. Then another WP-CRON instance starts.

That second instance sees that the lock is older than the sixty second timeout and claims the lock for itself. It then starts over at the beginning. So now you have two instances running – one holding the lock and one not holding the lock.

The first process unscheduled and rescheduled jobs as it went, but if the jobs are in the every-5-minutes queue, they are now ripe to be run again. So the second process starts them over again.

The first process gets to the end of the 20 minute job it was on, sees it no longer owns the lock, and quits. It does not reschedule the jobs that it unscheduled when it started. This can cause jobs to be lost and never be run again.

Also, because wp-cron unschedules jobs just before running them, if it were to die between doing that and the job completing, due to memory running out or something similar, the job would just be lost.

### Race Conditions

There is also a possible race condition. If another process both claims the lock after the first process checks it and before that process unschedules the next job, that job will be run twice. On a bogged down server, the likelihood of hitting that condition might be larger.

## What Does This All Mean

It means that CRON jobs can just randomly disappear – which is why we have our checks in place to warn when it looks as if DVI CRON jobs aren’t running.

We also offer an alternative method for triggering our CRON jobs – we call it [Better DVI Crons](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/wpcloud-deploy/better-wpcd-crons/).

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [WordPress POST Object Attributes and Variables](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/wordpress-post-object-attributes-and-variables/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240529143433/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
