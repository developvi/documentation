---
title: "Considerations When Using WP In A High-Availability Fault Tolerant Configuration"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Considerations When Using WP In A High-Availability Fault Tolerant Configuration
  parent: Fault Tolerant WP for AWS Scripts
  order: 2
---
When using WordPress in an HA fault-tolerant stack on AWS, you can usually use the same processes and procedures you would use on a single-server WP installation. But, there are going to be some things that you have to do very very differently and there are some processes that, if adopted, will make using a fault-tolerant WP configuration a little less frustrating.

## Plugins and Themes

The first process change we recommend you make is in uploading plugins and themes. For plugins and themes with a lot of small files in their zips, we strongly recommend that you upload these via sFTP. You’re less likely to get timeouts. The EFS (elastic file system) volume has a much higher latency so unzipping a lot of small files can take quite a bit of time. This can cause the web server to time out. Thus, sFTP is the recommended method for uploading plugins and themes.

Of course, if you’re integrating a GIT or other version control process into your workflow then this probably doesn’t matter as much.

## Backups

Do NOT install a backup plugin otherwise each server will try to run backups around the same time – not to mention they will attempt to overwrite backup records.

Instead, use AWS services to backup the EFS volume which contains the WP files and backup the RDS (database) server using the RDS snapshot/backup capabilities.

## Caching

You cannot use a page cache plugin such as WP ROCKET, NGINX ENABLER etc. to handle your page caching. This is because caching cannot be done on the individual servers. If you did that, you risk each server having a different version of the cached files – which means that each user could get different cached files. Instead, you need to setup CLOUDFRONT, CLOUDFLARE or other similar proxy service caches that sit **in front** of the entire HA cluster.

At some point you will want to designate and configure a server to serve as a a REDIS OBJECT CACHE – this can help performance and save on database queries. You will need to do some benchmarking to see if it helps in your particular instance because you will have to account for network latency – is the network latency worth the savings on DB queries? Usually the answer is yes but you should probably still do some bench marking just to be sure.

### More Topics In Fault Tolerant WP For AWS

*   [Installation and Configuration](https://web.archive.org/web/20240420014121/https://wpclouddeploy.com/documentation/fault-tolerant-wp/installation-and-configuration/)
*   [How The Scripts Work](https://web.archive.org/web/20240420014121/https://wpclouddeploy.com/documentation/fault-tolerant-wp/how-the-scripts-work/)
*   [Making Simple Changes](https://web.archive.org/web/20240420014121/https://wpclouddeploy.com/documentation/fault-tolerant-wp/making-simple-changes/)
*   [Default Configuration Reference](https://web.archive.org/web/20240420014121/https://wpclouddeploy.com/documentation/fault-tolerant-wp/default-configuration-reference/)
