---
title: "Making Simple Changes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Making Simple Changes
  parent: Fault Tolerant WP for AWS Scripts
  order: 4
---

Here are some simple changes you can quickly accomplish:

## Change the PHP version used

Search for ‘7.4’ in all files and replace with the version you want – eg: 8.1.

The search will probably result in something like this:

[![](https://web.archive.org/web/20240304143931im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-09.png)](https://web.archive.org/web/20240304143931/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-09.png)

So, you would open each file and just replace the 7.4 hits with 8.1 to switch to PHP 8.1 – all except the LAST hit – that obviously does not refer to PHP.

So, you can’t blindly do the search and replace – you do have to examine each hit to make sure it makes sense!

## Change The Instance Size

The default instance size for all servers is **m5.large**. So we search for that in all the files. You will likely only find one hit in the **env.sh** file. Change it to the size you want.

Just make sure those sizes are available in all the availability zones you’re using!

Inside that same _env.sh_ file, you will be able to change the OS image used (currently defaulting to Ubuntu 22.04 LTS) as well as the the database instance size (currently defaulting to db.t3.small).

## Additional Changes

Here are some additional changes you might consider:

*   Increase or decrease the number of PHP workers
*   Modify the WP site configuration to cache static assets, compress text etc.
*   Increase or decrease the memory allowed for each PHP worker
*   Automatically install plugins and themes from the repo or other url sources.

## More Advanced Changes

*   Create a custom AMI with the exact components you want in your server and specify that as the image id.
*   Expand EFS to replicate to multiple availability zones.
*   Add AWS BACKUPS (which backs up to VAULTS)

### More Topics In Fault Tolerant WP For AWS

*   [Installation and Configuration](https://web.archive.org/web/20240304143931/https://wpclouddeploy.com/documentation/fault-tolerant-wp/installation-and-configuration/)
*   [How The Scripts Work](https://web.archive.org/web/20240304143931/https://wpclouddeploy.com/documentation/fault-tolerant-wp/how-the-scripts-work/)
*   [Default Configuration Reference](https://web.archive.org/web/20240304143931/https://wpclouddeploy.com/documentation/fault-tolerant-wp/default-configuration-reference/)
*   [Considerations When Using WP In A High-Availability Fault Tolerant Configuration](https://web.archive.org/web/20240304143931/https://wpclouddeploy.com/documentation/fault-tolerant-wp/considerations-when-using-wp-in-a-fault-tolerant-configuration/)
