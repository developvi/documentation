---
title: "Dashboard"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Dashboard
  parent: 24-Powertools
  order: 2
---
When Powertools is installed and activated, a new menu option becomes available – “Dashboard”.

This provides a nice birds-eye view of what DVI has been up to. If logged in as the admin it shows a ton of data, a lot of which is pulled from the command and ssh logs.

[![](https://web.archive.org/web/20240529143151im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-205.png)](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-205.png)

[![](https://web.archive.org/web/20240529143151im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-207.png)](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-207.png)

When logged in as a regular user / owner, only the first few rows of data from the first screenshot will be shown.

## Reporting Groups

As an admin you can view this data by SERVER and APP groups and by a new field called **Reporting Group**.

The reporting group field is added to every server. This allows you to group the servers into collections that are different from SERVER and APP groups. For most organizations, SERVER and APP groups are all that’s needed but, once in a while, additional grouping options are needed and that’s where the Reporting Group field can help.

- - -

## Increasing Log Retention

If you plan on using this screen, you will likely want to keep your logs for much longer than the default. You can increase this as follows:

*   Go to **DevelopVIDeploy** → **Settings**
*   Click on the **LOGGING & TRACING** tab
*   Scroll down to the **AUTO TRIM LOG** field
*   Increase the value to an estimate that covers the time period you would like to retain.

- - -

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Netdata Integration](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
*   [Quickly Add Multiple Servers or Sites](https://web.archive.org/web/20240529143151/https://wpclouddeploy.com/documentation/powertools/quickly-add-multiple-servers-or-sites/)
