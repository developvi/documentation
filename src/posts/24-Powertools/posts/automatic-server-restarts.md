---
title: "Automatic Server Restarts"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Automatic Server Restarts
  parent: 24-Powertools
  order: 7
---
## Introduction

You can configure a global option to restart all your servers on a regular basis – eg: once per week. This is useful because many times background updates require a server to be restarted after they’re complete. Instead of manually doing this, you can just set it and forget it for your non-critical servers.

- - -

## Basic Configuration

*   Navigate to **DevelopVIDeploy**→ **SETTINGS** → **APP: WORDPRESS SETTINGS** → **SERVERS**
*   Scroll down to the **SERVER ACTIONS SCHEDULES** section
*   Select a schedule from the **RESTART SERVERS** drop-down field
*   Click the **SAVE** button at the bottom of the screen.

[![](https://web.archive.org/web/20240304144642im_/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-powertools-automatic-server-restart-04.png)](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/wp-content/uploads/2024/01/wpcd-powertools-automatic-server-restart-04.png)

- - -

## Overrides For Each Server

You can set a different restart schedule for each server in the RESTART SERVERS PERIODICALLY metabox:

[![](https://web.archive.org/web/20240304144642im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-server-restart-01.png)](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-server-restart-01.png)

You can also set the date and time the server will next restart. Future restarts will occur at the time specified.

- - -

## Custom Schedules

You can setup a custom schedule if one of the pre-installed ones are not suitable. DevelopVIDeploy includes four pre-defined schedules

*   Daily
*   Every 60 Min
*   Every 12 Hours
*   Every Week (on Saturday)

You can create one or more custom schedules on the **DevelopVIDeploy** → **SCHEDULES** screen. Just click the **ADD NEW** button at the top of the list.

- - -

## Notes

This feature depends on the local WP CRON – it does not add a server process to trigger the restart. Instead, when the WP CRON fires and conditions are satisfied, a request is sent to restart the server. This allows us to handle more complex conditionals for including and excluding servers from the restart process.

The downside to this is if, for some reason, the DVI CRON isn’t working, then the restart will not be triggered.

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Netdata Integration](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240304144642/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
