---
title: "Run Callbacks More Frequently"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Run Callbacks More Frequently
  parent: 24-Powertools
  order: 9
---
## Introduction

If you’ve been using DVI For a while now you know that callbacks is how we push data from the server to the DVI console. For example, the information in the HEALTH column in the server list is collected from the data sent by our callbacks processes. However, this only runs once per day.

Of course, you can change the schedule by logging into the server and using the CRONTAB command line tools to change the time at which the process will run. You can even add additional processes (eg: run it twice per day) But that’s still a little bit of a pain if you have a large number of servers.

With this new Powertools feature, you can setup a schedule that is different without logging into the server. And the core process will always run daily – anything defined here is in addition to that core process.

Also, there are some limitations that you should be aware of – read the NOTES section at the bottom of this document to understand what those are!

Note: Callbacks must be installed on the server for this feature to work. You can’t run them if they’re not already installed.

- - -

## Basic Configuration

*   Navigate to DevelopVIDeploy -> SETTINGS -> APP: WORDPRESS SETTINGS -> SERVERS
*   Scroll down to the SERVER ACTIONS SCHEDULES section
*   Select a schedule from the RUN CALLBACKS drop-down field
*   Click the SAVE button at the bottom of the screen.

This will run callbacks FOR ALL SERVERS using the schedule you chose.

- - -

## Overrides For Each Server

You can prevent the callbacks from running for any server. Each server has a new PERODICALLY RUN CALLBACKS metabox with an option to prevent the callbacks from running.

[![](https://web.archive.org/web/20240420005642im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-callbacks-01.png)](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-callbacks-01.png)

- - -

## Custom Schedules

You can setup a custom schedule if one of the pre-installed ones are not suitable. DevelopVIDeploy version 4.16 includes 4 pre-defined schedules

*   Daily
*   Every 60 Min
*   Every 12 Hours
*   Every Week (on Saturday)

You can create one or more custom schedules on the DevelopVIDeploy-> SCHEDULES screen. Just click the ADD NEW button at the top of the list.

- - -

## Notes

One of the differences between this type of scheduling and the Core plugin is the way in which the schedule functions and triggers the backup. With the core plugin, a CRON is set on the server itself to trigger the callbacks. With this function, the DVI WordPress Cron is used to trigger things. If, for some reason, the DVI CRON isn’t working, then the callbacks will not be triggered.

You should allow for enough time for the callbacks to complete between scheduled runs. We do not recommend anything less than 15 minutes and even that might be too low. Running callbacks is an intensive process so running it often can use up server resources that your sites might need. This is one of those tools that you can use to shoot yourself in the foot if you’re not careful!

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Netdata Integration](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240420005642/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
