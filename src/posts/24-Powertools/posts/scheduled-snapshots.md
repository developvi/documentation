---
title: "Scheduled Snapshots"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Scheduled Snapshots
  parent: 24-Powertools
  order: 3
---
## Introduction

Some server providers native dashboards have an option to take a snapshot or image of a server. However, few of them can do so on a scheduled basis and, even those that do, will either only retain a few snapshots, allow only a single schedule or simply not allow automatic deletion at all.

The **Scheduled Snapshots** module in Powertools aim to help overcome that limitation.

For providers where we can:

*   Take a snapshot and
*   Delete a snapshot

we can now offer automatic snapshots with automatic deletion and schedules. A list of supported providers are at the bottom of this page.

- - -

## Step 1: Create A Schedule

The first thing we need to do is create a schedule – eg: every 60 minutes. You can do this from the DevelopVIDeploy → SCHEDULES screen. Just click the ADD NEW button at the top of the (probably empty) list.

[![](https://web.archive.org/web/20240420010221im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-208.png)](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-208.png)

## Step 2: Assign the Schedule To Servers

In each server where you’d like to create automatic snapshots, assign a schedule in the SNAPSHOTS metabox:

[![](https://web.archive.org/web/20240420010221im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-209.png)](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-209.png)

Don’t forget to click the UPDATE button at the top right of the server screen to save your settings.

- - -

## View Snapshot List

Snapshots that are generated automatically from inside DevelopVIDeploy can be seen on the Snapshots list.

[![](https://web.archive.org/web/20240420010221im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-210.png)](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-210.png)

Snapshots that are deleted automatically will be removed from the list.

If you click into a snapshot there are a few things you can do:

*   Manually delete a snapshot
*   Set a snapshot to never be automatically deleted
*   Set a minimum date before which the snapshot cannot be deleted.

- - -

## Manual Snapshots

The core DVI functions include the ability for an admin to manually trigger a snapshot (from the server’s backup tab.). When that occurs, an entry will be placed in the snapshots list shown above. If DVI Powertools is not installed, no entry will be created (since that list does not exist without DVI Powertools).

- - -

## Deleting Snapshots

You can delete a snapshot directly from the snapshot list – just hover over an item and click the TRASH link. We will attempt to delete the snapshot from the provider if delete is supported.

If for some reason the delete fails and you cannot delete the record from the list, use the DELETE RECORD link instead.

- - -

## Supported Cloud Server Providers

Unfortunately, out of the 10 providers we support in the core plugin, we only offer scheduled snapshots for the following:

*   Vultr
*   AWS EC2
*   Hetzner
*   DigitalOcean (with limitations – deleting snapshots is not supported)
*   Linode – they will only keep a limited number of snapshots as “backups”. But we will show the full history of snapshots even if they don’t exist any more.
*   OpenStack – But see warning on how snapshots are handled in our OpenStack documentation.

For the other providers, we can add support for them under a custom development contract as long as they have snapshot create and delete api support.

- - -

## Other

Only snapshots created inside DVI will show up on the snapshots list. If you manually trigger a snapshot directly from your Server Providers’ dashboard, we will not have a record of it.

- - -

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Netdata Integration](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240420010221/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
