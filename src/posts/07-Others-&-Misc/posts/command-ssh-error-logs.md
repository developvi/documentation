---
title: "Command, SSH & Error Logs"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Command, SSH & Error Logs
  parent: 07-Others-&-Misc
  order: 8
---
There are four types of logs:

*   **Command Logs** – these log the results of long-running processes such as backups and clones.
*   **SSH Logs** – these log the results of shorter-duration action performed on a server or site (which are most of the actions)
*   **Error Logs** – these are populated when configured in settings.
*   **Pending Logs** – these show the status of certain background operations such as bulk operations and site/server creation after a WooCommerce purchase.

## Error Logs

You can configure what gets placed in the error logs as follows:

*   Go to WPCloud Deploy->Settings and click on the _Logging and Tracing_ tab.

In there you can decide what items you want to log (Errors, Debugging Statements or Other) and can further restrict by looking for particular pieces of text in the error/log messages.

By default, nothing is logged into the error log. It is solely a troubleshooting tool.

**DO NOT TURN THIS ON UNLESS OUR SUPPORT TEAM TELLS YOU TO DO SO! We know you want to do it but please do not do so without our support guidance!**
If you do decide to turn it on without our support team’s guidance, please do not then open a support ticket for anything you find in the logs. Why? Because lots of stuff will look scary that is perfectly normal.

### More Topics In Other & Misc

*   [Using Our DigitalOcean Template Image](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/digitalocean-template-image/)
*   [Using Our AWS EC2 Core Template](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-template-image/)
*   [AWS EC2 Premium Template](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-premium-template-image/)
*   [Translations](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/translations/)
*   [Moving The DVI Plugin To A New Server](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/moving-the-wpcd-plugin-to-a-new-server/)
*   [Simultaneous Dashboard Actions](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/simultaneous-dashboard-actions/)
*   [White Label](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/white-labelling/)
*   [Server Groups](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/server-groups/)
*   [Application (Site) Groups](https://web.archive.org/web/20240304142037/https://wpclouddeploy.com/documentation/other-misc/application-site-groups/)
