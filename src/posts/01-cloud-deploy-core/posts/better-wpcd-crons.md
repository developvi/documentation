---
title: "Better DVI Crons"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Better DVI Crons
  parent: 01-cloud-deploy-core
  order: 19
---
## Introduction

DevelopVIDeploy uses a lot of WordPress Cron jobs to keep things running smoothly.

However, the WordPress Cron process responsible for triggering the jobs has a severe limitation – it only triggers when there is traffic on the site.

This means that it’s almost impossible to consistently have Cron jobs that run every 5 minutes or every 1 minute on sites that are only used for admin purposes (eg: many DVI installations.)

But that’s exactly what DevelopVIDeploy needs – consistency in triggering Cron jobs.

The WordPress development team created an alternative Cron process though. This alternative deactivates the usual WP Cron trigger and uses a Linux Cron to trigger WP jobs. You can find more information with a [google search for DISABLE\_WP\_CRON](https://web.archive.org/web/20231207102049/https://www.google.com/search?q=DISABLE_WP_CRON).

The advantage of this alternative is two-fold:

*   For sites that are not visited frequently the jobs that are usually run with WP Cron will still run but on a consistent schedule
*   For sites with lots of traffic, Cron jobs will not be evaluated on every page load which provides a performance boost

Using this alternative WP Cron process is what we recommended up to DVI V 4.x. And whenever we created a server for customers to run DVI, we configured this alternative WP Cron on the server.

However, even this alternative has limitations. In particular:

*   It is possible for a Cron job to be completely deleted under certain circumstances. The admin might barely notice that it’s missing and the only way to get it (or them) back would be to deactivate and reactivate the DVI plugins.
*   With lots of jobs or jobs with a long running process, it is possible that the web server PHP process would timeout, leaving some jobs not executed.

In DevelopVIDeploy 5.0, we decided to take a page out of WordPress’s book and offer an alternative way to execute the DVI background Cron jobs. This is optional but is now the recommended method to use with DVI.

## The Concept

The idea is simple – you’ll set up a constant in wp-config.php (DISABLE\_DVI\_CRON) that will tell DVI to not schedule its regular Cron jobs.

Then, we’ll use a Linux cron to invoke wp-cli and trigger a DVI wp-cli specific command that will run the Cron jobs instead (calling the same action hooks that the standard DVI Cron jobs would have called.)

Below we’ll discuss how to set this up.

- - -

## Prerequisites

You should verify the following on the server where DVI is installed:

*   WP CLI should be installed and running globally.
*   WP CLI commands run against the DVI site should not be throwing errors (though warnings and notices are ok).

## Setup The WP-CONFIG.PHP Constant

Define DISABLE\_DVI\_CRON in the wp-config.php file on the site where DVI is installed

define( 'DISABLE\_WPCD\_CRON', true );

Next:

*   Deactivate the DevelopVIDeploy Plugin
*   Deactivate the DVI Powertools plugin (if installed and activated)
*   Reactivate the DevelopVIDeploy plugin
*   Reactivate the Powertools plugin (if it was installed and activated)

The process of deactivating and reactivating the two plugins removes any of the existing critical DVI Cron jobs affected by our new process.

## Setup The Linux Cron

Add a wp-cli command to your Linux Cron table (as the sudo/root user) to run **every 1 minute**.

run-one su - <youruser> -c "wp DVI wpcd\_wp\_cron\_actions"

The entry might look something like this:

\* \* \* \* \* run-one su - wpcd.cloud -c "wp DVI wpcd\_wp\_cron\_actions"

Notice the use of ‘run-one’. This prevents multiple Cron processes from running simultaneously and is very important!

Please double-check that the **run-one** package is installed on your system since not all Ubuntu images automatically include it. If it’s not the Cron will silently fail without any error messages.

Also notice the use of the _su – wpcd.cloud_ part of the command – this switches the user to the user named _dvi.cloud_ (your user will be different of course) and prevents wp-cli from running as root (which is dangerous).

The actual wp cli command added to the Linux Cron table might vary with your server configuration. The one shown above is the one that will work on any server that was created with the [wpcd bootstrap scripts](https://web.archive.org/web/20231207102049/https://WpCloudDeploy.com/documentation/ -deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/).

#### Crontab Variations & Tips

If you’re NOT using a server that was created with the DVI bootstrap scripts then it is likely that the system user for the site might not automatically be switched to the site folder. In that case something like this might be more appropriate for the crontab entry:

\* \* \* \* \* run-one su - _wpcd.cloud_ -c "**cd /var/www/yoursitefolder/html &&** wp DVI wpcd\_wp\_cron\_actions"

Notice the use of the **cd** command before running the **wp** command.

If all else fails, you might try the following alternative which will execute as the root or sudo user

\* \* \* \* \* run-one "cd **/var/www/yoursitefolder/html** && wp DVI wpcd\_wp\_cron\_actions --allow-root"

Change the **/var/www/yoursitefolder/html** portion of the entry to match the actual location of your DVI files.

#### Use of SUDO

On some servers where you’re not logged in as root, you might need to use ‘sudo’ in front of the crontab commands.

- - -

## How to tell if crons are disabled?

If you’ve added the DISABLE\_WPCD\_CRON constant to wp-config.php and deactivated and reactivated the plugins, then there should be almost no DVI jobs for the WP Cron process to run.

You can verify this as follows:

*   Install and activate the [WP CRONTROL](https://web.archive.org/web/20231207102049/https://wordpress.org/plugins/wp-crontrol/) plugin from wordpress.org on your DVI site.
*   Navigate to TOOLS → CRON EVENTS
*   Use the search box on the upper right to search for ‘dvi’

There should be no DVI processes scheduled (or maybe just one or two instead of the 6+ that are normally there).

## How To Tell If The DVI Cron Processes Are Still Firing?

Every time the DVI Cron jobs are run from a Linux Cron we write an entry to the error logs IF the appropriate logging flag is enabled.

You can temporarily enable this flag in the DevelopVIDeploy → SETTINGS → LOGGING AND TRACING tab.

In there, you’ll see an option for BETTER CORE CRONS. Just enable it and save settings.

[![](https://web.archive.org/web/20231207102049im_/https://WpCloudDeploy.com/wp-content/uploads/2022/10/wpcd50-logging-and-tracing-02.png)](https://web.archive.org/web/20231207102049/https://WpCloudDeploy.com/wp-content/uploads/2022/10/wpcd50-logging-and-tracing-02.png)

Then, every 1 minute or so, you should see a couple of new entries in the DevelopVIDeploy → ERROR LOGS screen:

[![](https://web.archive.org/web/20231207102049im_/https://WpCloudDeploy.com/wp-content/uploads/2022/10/wpcd50-logging-and-tracing-03.png)](https://web.archive.org/web/20231207102049/https://WpCloudDeploy.com/wp-content/uploads/2022/10/wpcd50-logging-and-tracing-03.png)

Don’t forget to turn off the flag in settings otherwise you’ll just be polluting your database with a bunch of entries that aren’t needed.

- - -

## Multisite

If DVI is installed on a multisite installation and in multiple subsites, you’ll need to make sure that your Linux Cron wp-cli command is executed on ALL the subsites where DVI is installed.

For example, you might use the following:

\* \* \* \* \* run-one su - <youruser> -c "cd /var/www/domain.com/htdocs && wp site list  --field=url | xargs -i -n1 wp wpcd\_wp\_cron\_actions --url=\\"{}\\" " > /dev/null 2>&1

Where you should replace <youruser> with the system user for the site and domain.com with your domain or folder for your site.

Or, if you really want to use the root user:

\* \* \* \* \* run-one su - root -c "cd /var/www/domain.com/htdocs && wp site list --allow-root --field=url | xargs -i -n1 wp DVI wpcd\_wp\_cron\_actions --url=\\"{}\\" --allow-root" > /dev/null 2>&1

- - -

## Troubleshooting

After installing this it is possible that it works for a while and then you start to see the DVI WARNING about CRONS not running. This is usually because the _run-one_ process is stuck for some reason.

You can handle this by first identifying the process id that is stuck:

ps -C run-one

If you see an ID in the PID column then it is possible that that the _run-one_ process is stuck. To confirm, wait about 30 seconds and run the command again – if it shows the same PID then it is likely that the process is stuck for some reason.

You can also run this command to see if any process that include ‘wp’ is running:

ps aux | grep -i wp

If you run that command twice, waiting 30 seconds in between and you see the ‘wpcd\_wp\_cron\_actions’ string both times then it’s likely the command is stuck.

In either case the simplest solution to this is to restart the server.

- - -

## Notes

*   If you change the domain for your DVI site you will likely need to change the Linux crontab entry to point to the new domain.
*   If it seems as if things aren’t working, double check that the **run-one** package is installed – some Linux images/distributions do not automatically include it. If not, you can use the **sudo apt-get install run-one** command to install it.

- - -
