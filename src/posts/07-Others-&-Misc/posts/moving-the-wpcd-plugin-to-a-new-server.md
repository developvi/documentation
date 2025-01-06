---
title: "Moving The DVI Plugin To A New Server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Moving The DVI Plugin To A New Server
  parent: 07-Others-&-Misc
  order: 5
---
So, you have DVI up and running but now you want to move it to a new site or server. Maybe you even want to change its domain.

Since it is just a WordPress plugin, all you have to do is backup your existing site and restore it to your target server. You can use any WordPress backup and restore tool to do this – we use UPDRAFT PLUS internally but any other reputable backup & restore plugin should be able to do the trick for you.

Before you move your site, you should ensure that the new location will satisfy all the [requirements](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/wpcloud-deploy/requirements/) for a DVI server / site. This includes making sure server time outs are increased, REST API endpoints are accessible, ports are open etc. A common issue we see is that the target server / site isn’t vetted properly so when the move is complete, many quirky things start to occur.

While it is easy to move a WP site, you should not consider doing so unless it’s absolutely necessary. DVI is a critical piece of your infrastructure and it should be respected and treated as such!

For the best results, we strongly recommend you use our support team and contract services to help with any moves.

A few things to check after your move:

1.  Make sure that your encryption key in wp-config.php has been copied from your original site/server
2.  Since your IP address changed you should check that any IP based restrictions for your API at your server provider (s) include your new sites’ IP Address.
3.  If your domain changed, then you will need to deactivate and reactivate any services that call back into your server to report their status. This includes Backups and the Callback services under your Servers’ callback tab.

Some providers we know that offer IP based restrictions for their API are:

*   Vultr
*   Upcloud

### More Topics In Other & Misc

*   [Using Our DigitalOcean Template Image](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/digitalocean-template-image/)
*   [Using Our AWS EC2 Core Template](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-template-image/)
*   [AWS EC2 Premium Template](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/aws-ec2-premium-template-image/)
*   [Translations](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/translations/)
*   [Simultaneous Dashboard Actions](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/simultaneous-dashboard-actions/)
*   [White Label](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/white-labelling/)
*   [Command, SSH & Error Logs](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/command-ssh-error-logs/)
*   [Server Groups](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/server-groups/)
*   [Application (Site) Groups](https://web.archive.org/web/20240304140444/https://wpclouddeploy.com/documentation/other-misc/application-site-groups/)
