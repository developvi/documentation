---
title: "Common Server Deployment Issues & Error Messages"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Common Server Deployment Issues & Error Messages
  parent: 06-Troubleshooting-and-FAQs
  order: 6
---
Sometimes, when attempting to deploy a server, it might look as if the process has “hung”. Most times it has not – it just takes a while to deploy a server. The time could be from 20 minutes to as long as 45 minutes depending on the cloud provider and the size of the server being deployed. Our software stack alone can take 15+ minutes to install.

But, that doesn’t mean that you might not run into issues. Here are some common ones:

### Message: Unfortunately we could not start deploying this server – most likely because of an error from the provider api.

Symptom: You see the following message on your screen after attempting to create a server:

*   Unfortunately we could not start deploying this server – most likely because of an error from the provider api (an example of this is shown below)

[![Example of error message that can appear when attempting to deploy a server from DVI](https://web.archive.org/web/20240420004029im_/https://wpclouddeploy.com/wp-content/uploads/2021/07/wpcd-v4-126.png)](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/wp-content/uploads/2021/07/wpcd-v4-126.png)

There are three common causes for this:

1.  The private key is malformed in the settings screen
2.  The API Keys or other credentials for the provider are not correct
3.  The requested server size is not available in the region

**Malformed Private Key**

_If you copy your key directly from the SSH console (eg: by CATing it out or opening in NANO/VIM and then copy-and-paste), it will end up with unwanted spaces when pasted into our settings screen. You should always download your original key-pair files and open the private key file in a notepad application (not a word-processing application) and then copy-and-paste from there._

**Invalid Server Size**

You can log into your cloud provider and try to provision a server directly from their console using the same size and region you’re trying to deploy with DVI. If you don’t see the size you’re trying to provision with DVI that will confirm that the server size is the underlying cause of the issue. You can then try a different size/region combination.

- - -

### Message: Error updating xxx or Error installing xxx. Please delete this server and restart the process.

Symptom: You see any of the following messages:

*   Error updating repositories. Please delete this server and restart the process.
*   Error installing dos2unix. Please delete this server and restart the process.
*   Error installing vnstat. Please delete this server and restart the process.

These mean what they say – something went wrong and it was serious enough that you need to delete the in-process server and start over again.

This tends to happen most often with Digital Ocean servers. What we have realized is that the droplets or VMs that these errors occur on are generally the most unstable. Getting the error now prevents you from more serious issues later on down the line when the VM or droplet really degrades and you lose data.

- - -

### Attempting To Use Your Local PC For Deployment

Most personal computers cannot be accessed from the public internet so the callbacks that the server deployment process uses will simply not work.

- - -

### Stuck at “_sudo: dos2unix: command not found_“

**Symptom:** You see the following message in the black “terminal” window:

*   sudo: dos2unix: command not found

This is the real deal – it is stuck. This tends to happen most often with DigitalOcean servers.

To resolve:

1.  Click on the ALL CLOUD SERVERS Main menu to see the server list.
2.  DELETE the server that you were trying to create – you can do this by hovering over the server record and clicking the TRASH link. This should also delete the in-process server at the cloud provider.
3.  Retry creating the server again.

- - -

### Stuck at _“E: Could not get lock /var/lib/dpkg/lock-frontend – open (11: Resource temporarily unavailable)”_

**Symptom:** You see the following messages in the black “terminal” window:

*   _E: Could not get lock /var/lib/dpkg/lock-frontend – open (11: Resource temporarily unavailable)_
*   _E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?_

And, these messages are the last line in the “terminal” window – no more log entries are being printed.

This is the real deal – it is stuck. This tends to happen most often with Digital Ocean servers.

To resolve:

1.  Click on the ALL CLOUD SERVERS Main menu to see the server list.
2.  DELETE the server that you were trying to create – you can do this by hovering over the server record and clicking the TRASH link. This should also delete the in-process server at the cloud provider.
3.  Retry creating the server again.

- - -

### Message In “terminal”: _Warning: 3 database(s) sources were not found_

You see the following message in the “terminal” window:

_Warning: 3 database(s) sources_
_were not found, (but were created)_
_please investigate._

This is just a warning and not an issue. You should see additional log entries printed immediately after this indicating that the installation is continuing.

- - -

### Message In “terminal”: _Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal_

You see the following message in the “terminal” window on a number of lines:

_Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal._

This is informational and not an issue. Its just complaining because the process isn’t really running in a terminal with a real screen.

- - -

### Message In “terminal”: _unable to initialize frontend: Dialog_

You see the following message in the “terminal” window on a number of lines:

_unable to initialize frontend: Dialog_

This is informational and not an issue. Its just complaining because the process isn’t really running in a terminal with a real screen.

### More Topics In Troubleshooting & Faqs

*   [Fixing Error 413: REQUEST ENTITY TOO LARGE](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/fixing-error-413-request-entity-too-large/)
*   [Reasons Sites Fail To Deploy](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-sites-fail-to-deploy/)
*   [Reasons Servers Fail To Deploy](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/reasons-servers-fail-to-deploy/)
*   [Too Many Redirects With CloudFlare](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/too-many-redirects-with-cloudflare/)
*   [Server FAQs](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/server-faqs/)
*   [Health Column Messages](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/health-column-messages/)
*   [Troubleshooting The "Critical Cron" Email And Related Message Alerts](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/troubleshooting-the-critical-cron-email-alerts/)
*   [Handling dpkg messages in your SSH Logs](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/handling-dpkg-messages-in-your-ssh-logs/)
*   [Ubuntu 20.04 Notes](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-20-04-notes/)
*   [Ubuntu 18.04 Notes](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-18-04-notes/)
*   [Ubuntu 22.04 Notes](https://web.archive.org/web/20240420004029/https://wpclouddeploy.com/documentation/troubleshooting-and-faq-parent/ubuntu-22-04-notes/)
