---
title: "Default Configuration Reference"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Default Configuration Reference
  parent: Fault Tolerant WP for AWS Scripts
  order: 5
---
Here is the default configuration with the out-of-the-box scripts:

## AWS General

*   Server Size: m5.large
*   DB Server Size: db.t3.small
*   Server Availability Zones: 2
*   EFS Zones: 1
*   EFS mount point: efs
*   Keypairs: 1
*   Security Groups: 1
*   Load Balancer:
*   AWS WAF: None
*   CloudFormation Stacks: 1

## PHP Configuration

Default PHP.INI Except for the following changes:

*   memory\_limit: 512M
*   max\_input\_vars: 5000
*   max\_execution\_time: 300
*   post\_max\_size: 64
*   upload\_max\_filesizse: 64

## WP Configuration

*   table\_prefix: wp
*   debug flags: false
*   WP\_AUTO\_UPDATE\_CORE: minor
*   WP\_MEMORY\_LIMIT: 512M
*   WP\_MAX\_MEMORY\_LIMIT: 512M
*   CONCATENATE\_SCRIPTS: false
*   DISALLOW\_FILE\_EDIT: true

### More Topics In Fault Tolerant WP For AWS

*   [Installation and Configuration](https://web.archive.org/web/20240304144343/https://wpclouddeploy.com/documentation/fault-tolerant-wp/installation-and-configuration/)
*   [How The Scripts Work](https://web.archive.org/web/20240304144343/https://wpclouddeploy.com/documentation/fault-tolerant-wp/how-the-scripts-work/)
*   [Making Simple Changes](https://web.archive.org/web/20240304144343/https://wpclouddeploy.com/documentation/fault-tolerant-wp/making-simple-changes/)
*   [Considerations When Using WP In A High-Availability Fault Tolerant Configuration](https://web.archive.org/web/20240304144343/https://wpclouddeploy.com/documentation/fault-tolerant-wp/considerations-when-using-wp-in-a-fault-tolerant-configuration/)
