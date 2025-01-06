---
title: "Automatic Backups On A Different Schedule"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Automatic Backups On A Different Schedule
  parent: 24-Powertools
  order: 8
---
## Introduction

We have a number of ways to trigger backups in the core plugin. But, sometimes even that is not enough.

For example, basic core backups always run at the same time every day for all servers. And it only runs once per day.

The [advanced backups](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/) gives you more flexibility but require you to use the command line. Still, this runs at the same time every day as well.

Of course, you can change the schedule of either backup option by logging into the server and using the CRONTAB command line tools to change the time at which the backup process will run. But that’s still a little bit of a pain if you have a large number of servers.

With this Powertools backup feature you can schedule backups to run on a different schedule and to run multiple times each day (eg: every 4 hours). However, please read the notes section at the bottom of this document to understand how this differs from core backups.

- - -

## Setup

Before using this feature, you must have [setup your AWS S3 credentials and default bucket in the settings area](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/) (DevelopVIDeploy → SETTINGS → APP: WORDPRESS SETTINGS → BACKUP AND RESTORE). Alternatively, you can setup S3 credentials for the each individual server in the BACKUP & RESTORE tab for the server. Either option will push S3 credentials and bucket information to the server and prepare the server for backups.

After that, setting up this feature is simple – just set a schedule on the RUN BACKUPS PERIODICALLY metabox. This metabox only appears if the POWERTOOLS add-on is activated.

[![](https://web.archive.org/web/20240420002803im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-backups-01.png)](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-backups-01.png)

- - -

## Custom Schedules

You can setup a custom schedule if one of the pre-installed ones are not suitable. DevelopVIDeploy version 4.16 includes 4 pre-defined schedules

*   Daily
*   Every 60 Min
*   Every 12 Hours
*   Every Week (on Saturday)

You can create one or more custom schedules on the DevelopVIDeploy → SCHEDULES screen. Just click the **ADD NEW** button at the top of the list.

- - -

## Notes

One of the differences between this type of backup scheduling and the Core plugin is the way in which the schedule functions and triggers the backup. With the core plugin, a CRON is set on the server itself to trigger backups. With this function, the DVI WordPress Cron is used to trigger things. If, for some reason, the DVI CRON isn’t working, then these types of backups will not be triggered.

You should allow for enough time for the backups to complete between scheduled runs. For example, if you have a large site, it’s not a good idea to set a backup to run every 15 minutes.

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Netdata Integration](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240420002803/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
