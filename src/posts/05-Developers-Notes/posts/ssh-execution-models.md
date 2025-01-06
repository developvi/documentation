---
title: "SSH Execution Models"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: SSH Execution Models
  parent: 05-Developers-Notes
  order: 18
---
DevelopVIDeploy uses a [PHP ssh library](https://web.archive.org/web/20240529160218/http://phpseclib.sourceforge.net/) to connect to WordPress servers in order to execute commands and collect information.

There are three execution models we use to manage this.

## 1\. Direct Execution

Direct execution is used for commands that we reasonably believe will take a short amount of time to execute. Most commands fall under this umbrella. These include:

*   Enabling / Disabling a site
*   Enabling/ Disabling SSL
*   Getting diskspace used
*   Adding/Updating/Removing sFTP users
*   etc.

Within the plugin code you will see this handled as follows:

$result = $this->execute_ssh( 'generic', $instance, array( 'commands' => $run_cmd ) );

Basically we submit a command to the server and wait the result. We then evaluate the result and do some stuff.

This is pretty straightforward. Unfortunately, if you want to give feedback to users when the command has a lot of output or is taking a long time to run, you can’t do this. If you try, the user will either think the command is not working/is frozen OR the command will time out and the user will see an error.

Thus, for long running commands, we need a more complex process in which we can offer feedback to the user and prevent timeouts.

Before going into the two different types of long-running commands we implement, lets get some terminology down:

There are two servers involved:

1.  The server where the DevelopVIDeploy plugin is running and
2.  The WordPress server being created or managed by the DevelopVIDeploy plugin.

So, we need to name these two servers so that its clear which server we are talking about at any one time.

1.  The server where the DevelopVIDeploy plugin is running shall be called the **DevelopVIDeploy plugin server**
2.  The WordPress server being created or managed by the DevelopVIDeploy plugin shall be called, simply, the **Target WordPress server**

## 2\. Async Execution Type 1 For Long Running Commands

This model is used in things like DEPLOYING A NEW SERVER and INSTALLING A NEW WordPress SITE. It works using a set of timers and cron processes and goes something like this:

*   UI (browser) submits an AJAX command to start a process – eg: to deploy a new cloud server. At the same time a javascript TIMER is started – default is every 5 seconds. The command to run is relayed to the _WPCloudDeploy Plugin Server_ via the AJAX call.
*   When the _WPCloudDeploy Plugin server_ gets the call it gets to work doing the thing.
    *   If necessary it performs an interim step to create the _Target WordPress server_ at the cloud provider (this is only necessary when creating a new server otherwise this step is skipped)
*   The server CPT record is stamped with some metavalues to let the world know that an action is in-progress and a message and success flag is returned to the AJAX call.
    *   If it’s a new server being deployed, the server CPT record is first created
*   A WP CRON process kicks off every 1 minute on the _WPCloudDeploy Plugin server._ It’s job is to check all server records to see if an item is in progress or if an item needs to be started. If it finds a match, it either starts the item or collects the logs and stores them in the database log records.
    *   An example where an item might need to be started would be installing the LEMP tech stack after a server has been created by the cloud server provider.
*   Now, each time the JS timer fires (remember it fires every 5 seconds), it sends a request to the _WPCloudDeploy plugin server_ to get logs about the action running. If logs are found on the server, they are sent back to the browser which in turn shows them to user in a ‘terminal’ window.

So how does this whole cycle end?

It ends when the _Target WordPress server_ that we are talking to sends us back a notification via a REST API call. When we receive this call, we mark the command as completed. The next time the JS UI timer asks for logs, the _WPCloudDeploy Plugin server_ then responds with the logs as well as an indication that the command is completed. Upon receipt of the “command done” indicator, the browser can then turn off its timer to stop polling the _WPCloud Deploy Plugin server_ for logs.

## 3\. Async Execution Type 2 For Long Running Commands

This model is used in things like BACKUP and RESTORE. It closely resembles the TYPE 1 model and, just like it, works using a set of timers and cron processes and goes something like this:

*   UI (browser) submits an AJAX command to start a process – eg: start a backup.
*   PHP code on the _WPCloud Deploy Plugin server_ kicks off the ssh request which includes a callback function. It also stamps the server CPT records with some metavalues to let the world know that a long running process is in-progress. It then returns a value to the UI (browser) which effectively tells the javascript code – “hey, this is an async function so poll me for log files”.
*   A WP CRON process kicks off every 1 minute on the _WPCloud Deploy Plugin server,_ checking all server records to see if an item is in progress and, if so, collect the logs and store it in the database log records.
*   The UI (browser) has a timer running (set to 30 seconds) that polls the server to read logs that might have been written by the CRON process. If it finds logs, it sends them back to the browser which in turn shows them to user in a ‘terminal’ window.

So how does this whole cycle end?

It ends when the _Target WordPress server_ that we are talking to sends us back a notification via a REST API call. When we receive this call, we mark the command as completed. The next time the UI timer asks for logs, the _WPCloudDeploy Plugin server_ then responds with the logs as well as an indication that the command is completed. The browser can then turn off its timer.

## Notes

So, you must be asking yourself, how does the Target WordPress server know which REST API endpoint to use and when to call it?

Good Question!

95% of the time, when we submit a command to a Target WordPress server, its not just one command. Its a series of chained commands. They might look something like this:

sudo -i -E cd /root &&
sudo -E \\rm -f 03-disable-remove-site.sh &&
sudo -E wget --no-check-certificate -O 03-disable-remove-site.sh https://wpclouddeploypluginserver.com/wp-content/plugins/wp-cloud-deploy/includes/core/apps/wordpress-app/scripts/v1/raw/03-disable-remove-site.txt &&
export action=remove domain=cf108.wpvix.com &&
sudo -E dos2unix 03-disable-remove-site.sh &&
sudo -E bash 03-disable-remove-site.sh

For long running commands, we include a sub-command to call the rest api endpoint as the very last command in the chain – see the BOLD line in the code sample below:

echo "done" && {
sudo -i -E cd /root &&
sudo -E apt-get update -yqm >> wordpress-app_prepare_server.log.intermed 2>&1 &&
sudo -E apt-get install -yqm dos2unix sendmail >> wordpress-app_prepare_server.log.intermed 2>&1 &&
sudo -E apt-get install -y vnstat >> wordpress-app_prepare_server.log.intermed 2>&1 &&
sudo -E wget --no-check-certificate -O 01-prepare_server.sh https://wpclouddeploypluginserver.com/wp-content/plugins/wp-cloud-deploy/includes/core/apps/wordpress-app/scripts/v1/raw/01-prepare_server.txt &&
export interactive=no &&
sudo -E dos2unix 01-prepare_server.sh &&
sudo -E bash 01-prepare_server.sh >> wordpress-app_prepare_server.log.intermed 2>&1 &&
sudo -E mv wordpress-app_prepare_server.log.intermed wordpress-app_prepare_server.log.done &&
**sudo -E wget -q https://wpclouddeploypluginserver.com/wp-json/wordpress-app/v1/command/82482/prepare_server/completed/1586126728/**;
} > /dev/null 2>&1 &
