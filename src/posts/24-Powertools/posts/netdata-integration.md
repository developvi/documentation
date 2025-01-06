---
title: "Netdata Integration"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Netdata Integration
  parent: 24-Powertools
  order: 4
---
## Introduction

[Netdata](https://web.archive.org/web/20240420003351/https://www.netdata.cloud/) is a free cloud service that aggregates signals from all your servers into a centralized dashboard. The unique thing about it is that the cloud services are indeed free – right now for an unlimited number of servers.

The reason that they can make it free is because the signal data is not actually stored on their servers. It’s stored on your servers and pushed to their centralized dashboard on demand.

[![](https://web.archive.org/web/20240420003351im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-232.png)](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-232.png)

If you have more than a few servers this is a GREAT tool. In many ways it’s better than Monitorix since you cannot get an aggregated view of all your Monitorix dashboards.

- - -

## Before You Install Netdata on a server

Before you install Netdata on your servers, you should sign up for a Netdata account and collect two pieces of information:

*   Your Claim Token
*   Your Rooms Token

Your claim token is what the Netdata cloud services uses to identify your servers – it should be kept secret otherwise anyone can add their servers to your space.

A room is simply a collection of servers and Netdata creates one for you automatically. If you use that room token, your server will be placed into it automatically. You can, of course, create your own rooms and use those room tokens instead. You can use different rooms tokens for different servers if you so desire.

You should only install Netdata on a server with at least 2 GB of RAM. And machines/VMs with a minimum of 2 vCPUs is strongly recommended.

- - -

## Install Netdata

If Powertools is installed and activated there will be a new Netdata tab on your server. There are five fields you need to fill in, two of which help you connect to your Netdata cloud account.

The first three fields allow you to access the Netdata dashboard locally for your server without using your Netdata cloud account.

Please read that last sentence again. _It means that you have TWO ways to access data for your server_

1.  Using your Netdata cloud account and
2.  By directly navigating to a local Netdata dashboard.

[![](https://web.archive.org/web/20240420003351im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-211.png)](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-211.png)

If you plan on NEVER navigating to your local dashboard you can fill in the domain field with a nonsensical domain. But if you do want to view the local dashboard then that domain needs to be any real domain (such as netdata-server-01.yourdomain.com) and its DNS needs to be pointed to the servers’ ip address.

Note that it takes about 10 minutes to install Netdata. It downloads a lot of components. When running it can take between 3% and 10% of your CPU cycles on a single processor core.

- - -

## Netdata Actions

After Netdata is installed, it should automatically appear in your Netdata cloud account. Most users will login to the cloud account and view server information there.

But, if you want to view the local dashboard on a regular basis you should install an SSL certificate – that option will appear after installation.

And, of course, you can remove it \[Netdata\].

[![](https://web.archive.org/web/20240420003351im_/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-212.png)](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/wp-content/uploads/2021/12/wpcd-v4-212.png)

- - -

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Recurring Site Images](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Home Page Images](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/home-page-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240420003351/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
