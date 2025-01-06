---
title: "How The Scripts Work"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How The Scripts Work
  parent: Fault Tolerant WP for AWS Scripts
  order: 3
---
There are an extensive set of files that comprise the scripts – most of which are bash scripts ending in .sh.

[![](https://web.archive.org/web/20240304140014im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-05.png)](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-05.png)

The entry point into the scripts is _install.sh._

It automatically pulls in and uses scripts in the subfolders. The subfolders have the following scripts:

[![](https://web.archive.org/web/20240304140014im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-06.png)](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-06.png)

[![](https://web.archive.org/web/20240304140014im_/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-07.png)](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/wp-content/uploads/2023/10/wpcd-wp-loadbalance-07.png)

You can probably figure out what each of these scripts do simply from their names – _install\_nginx.sh_ for example, handles installing NGINX on a server instance.

The CloudFormation template is in the TEMPLATES folder.

Each bash script (scripts ending in .sh) ultimately feeds information into the CloudFormation template.

### More Topics In Fault Tolerant WP For AWS

*   [Installation and Configuration](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/documentation/fault-tolerant-wp/installation-and-configuration/)
*   [Making Simple Changes](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/documentation/fault-tolerant-wp/making-simple-changes/)
*   [Default Configuration Reference](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/documentation/fault-tolerant-wp/default-configuration-reference/)
*   [Considerations When Using WP In A High-Availability Fault Tolerant Configuration](https://web.archive.org/web/20240304140014/https://wpclouddeploy.com/documentation/fault-tolerant-wp/considerations-when-using-wp-in-a-fault-tolerant-configuration/)
