---
title: "Metadata Syncing"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Metadata Syncing
  parent: 07-Others-&-Misc
  order: 4
---
## Introduction

“Data Syncing” in the context of this feature simply means copying your SERVER & SITE metadata stored in DVI to another site that is also running DVI.

With this feature you can always be sure that you have a backup of your DVI data ready to be up and running in minutes. You don’t even have to go through a normal WordPress restore process. With just a couple of clicks you can restore your data on the target site and be ready to go!

But the most convenient aspect of this feature is that it can be configured to automatically run on a periodic basis – eg: once per day.

## How It Works

The overall process is, conceptually, pretty simple – we extract the Server & Site data from our custom post types, package it up, encrypt it with a key you provide and send it via a REST api call to another WordPress site that is also running DVI. When it’s time to restore the data, you simply click a link, enter your encryption key and all your data is restored.

There are some nuances and limitations of course but we’ll cover those below.

The overall goal is that you always have a copy of your server and site meta-data located else-where and ready to use within a few minutes.

You could achieve that same thing with a standard backup and restore process but that takes longer and you end up restoring everything on your site, not just the DVI data – which might not be what you want.

**Warning: You should still run regular backups of your primary DVI site. A regular backup is the safest way to secure your data!**

## What You Need

The main pre-requisite for this feature is that you have a second site where DVI is installed. This second site will be your “destination” site or your “target” site. DVI data will be sent from your primary (“origin”) site to this destination site.

## Configure Data Transfer To Your Destination

After you have set up a destination site to receive a copy of your server and site metadata, you’ll need to configure your primary site to push that data. To do this:

*   Go to WpCloudDeploy->Settings.
*   Click on the **Data Sync** tab.
*   Click on the **Send Data** tab.
*   The first part of the screen will ask for your destination server information: The _URL of the destination site (including the http:// or https:// prefix)_, an _encryption ke_y that will be used to encrypt your data and the _user id_ and _password_ of your admin account on the destination site.
*   Decide if you want to export regularly on an hourly or daily interval and whether you want to send data from your settings screen (usually you do want to do that).
*   Finally, scroll all the way down to the blue SAVE SETTINGS button and click it.

[![](https://web.archive.org/web/20240420005824im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-057.png)](https://web.archive.org/web/20240420005824/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-057.png)

If everything is correctly configured you should start to see data show up on your destination site under the SETTINGS screen.

You can trigger an immediate push to the destination site by clicking the PUSH button.

## Destination Site Operations & Restoring Data

When the data arrives on the destination site, it remains encrypted in a compressed format in the database. You need to explicitly run a quick restore operation in order to use it.

To restore data:

*   Go to WpCloudDeploy->Settings.
*   Click on the **Data Sync** tab.
*   Click on the **Received Data** tab.
*   Scroll down to the RECEIVED FILES section.
*   Click on the RESTORE next to the latest file (or any other file).
*   You will see a popup that asks you to enter your encryption key – this is the same key you entered at your origin site.
*   If the key is entered correctly the data will be restored and you should see your server and site information.

There are two things to be aware of:

1.  If you didn’t transfer your settings, you’ll need to re-enter them in your settings screen before you can perform operations on your servers and sites.
2.  If you did choose to transfer your settings then you will need to enter your wp-config.php encryption key **from the source/origin** site _**into the destination server wp-config.php**_ file. OR, if you do not have an encryption key entered in your destination site’s wp-config.php already, you can enter the key under the DESTINATION OPERATIONS->ENCRYPT KEYS section where it will be stored in the database. Though, we strongly recommend that you use the wp-config.php method. If you do not do this, your SETTINGS data will be worthless.

[![](https://web.archive.org/web/20240420005824im_/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-058.png)](https://web.archive.org/web/20240420005824/https://wpclouddeploy.com/wp-content/uploads/2020/12/wpcd-v4-058.png)

## Notes

1.  It is important to realize that **ONLY DevelopVIDeploy data is pushed to the destination site**. If you’re using other plugins, themes, add-ons etc. and they are mission critical to your operations, then you will need to go through a standard backup-restore process in order to get a new DVI site up and running. But, if your primary DVI site is only used for managing your servers and sites then this feature, with some advance planning, will be very useful for getting a recovery site up and running within minutes.
2.  Your destination site will likely have a different URL than your primary site. Which means that your server call-backs will still be attempting to report data to your primary site. If you intend to keep using a destination site as your primary site after a failure, you have two choices: 1. Change the URL of your destination site to match /replace the primary site or 2. Reset your callbacks by turning them off and back on again in the destination console – this includes turning backups off and on again as well.
