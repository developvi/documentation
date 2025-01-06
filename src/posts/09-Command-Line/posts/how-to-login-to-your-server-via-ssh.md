---
title: "How To Login To Your Server Via SSH"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Login To Your Server Via SSH
  parent: 09-Command-Line
  order: 6
---
Sometimes, the only way to get something accomplished is via the command line. To get there, you need:

*   An SSH Client (software)
*   The ‘root’ user name for your server – usually this is ‘root’ or ‘ubuntu’ but can be something different (eg: when using Google Cloud or Azure).
*   The private key for your ‘root’ user.

## How To Find Your User Name

For most providers, the user name is _root_.

Certain providers such as EC2 & Lightsail use the _ubuntu_ user.

Other services might have unique user names:

*   Azure: wpcdadmin

## How To Find Your Private Key

Your private key is in the DevelopVIDeploy → SETTINGS → CLOUD PROVIDERS tab.

There is usually a field where you entered your private key for the root user for the server.

[![](https://web.archive.org/web/20240529145252im_/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-v4-250-1.png)](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/wp-content/uploads/2022/02/wpcd-v4-250-1.png)

## SSH Client

Now that you have your user name and private key, you need an SSH client / software. There are many such as Putty, Bitvise and Termius. And, most operating systems today include an SSH client that can be accessed via the command line using an ‘ssh’ command.

However, if you’re reading this document then we’ll assume you’re newer to ssh. So it’s easier if you can use an app with a GUI (graphical user interface).

In our opinion the easiest app with a GUI is [TERMIUS](https://web.archive.org/web/20240529145252/https://termius.com/). Download links for the various operating systems are usually in the footer of the Termius website.

Just download the version for your operating system, install it and go through the on-boarding process (which usually requires setting up a Termius account).

After installation, we recommend that you DISABLE syncing of your keys in Termius. With syncing turned on, your keys are encrypted and uploaded to the Termius servers so that you can use them on any machine where you install Termius including your phones and tablets. But that means you are depending on Termius’ encryption to keep your keys secure. If you’re not comfortable with this you can disable syncing as follows:

*   Fire up Termius and login if prompted.
*   Click the “gear” icon on the upper left. This will bring you to a screen with a menu running down the left hand side of the Termius window.
*   Click on the ACCOUNT option in the menu.
*   Toggle the SYCHRONIZATION switch to the ‘off’ position to disable syncing. This will keep your keys only on the machine on which Termius is currently installed and will not push them to the Termius servers.

## Logging Into Your Server With Termius

Once installed and an account created, there are three steps needed to connect to your server:

1.  Add your private key to Termius
2.  Add your server details to Termius
3.  Connect to your server

### 1\. Add Your Private Key To Termius

*   Fire up Terminus and login if prompted.
*   Click on the “gear” icon on the upper left. This will bring you to a screen with a menu running down the left hand side of the Termius window.
*   Select the KEYCHAIN option in the menu.
*   Click the NEW KEY button at the top of the central panel and then click the IMPORT OR PASTE A KEY option from the resulting menu. This will open up a panel with a few blank fields on the right hand side of the Termius window
*   At the top of the panel on the right hand side you should set a name for the key in the SET A LABEL field.
*   Add the passphrase (if any)
*   Copy the PRIVATE KEY you obtained from the “How to find your private key” section above and paste it into the PRIVATE KEY field in Termius.
*   Look for a tiny checkmark next to the label you added at the top of the panel – this will indicate that your changes have been saved. (Termius automatically saves changes so there is no equivalent of a SAVE button.)
*   Click the ESC key to return back to the main Termius Window.

### 2\. Add Your Server To Termius

*   Click on the HOSTS menu option on the left menu of the main Termius window.
*   Click the NEW HOST button at the top of the central pane. This will open up a panel with a number blank fields on the right hand side of the Termius window.
*   Fill in the SET A LABEL field at the very top of the right hand panel – this can be any name and will be used to identify your server in the server list.
*   Fill in the address field with the IP address of your server.
*   Fill in the user name field with the root or sudo user name (usually ‘root’ or ‘ubuntu’ but can be something else for certain server providers.)
*   Fill in the password for the user.
*   Look for a tiny checkmark next to the label you added at the top of the panel – this will indicate that your changes have been saved.

### 3\. Connect To Your Server With Termius

*   Click on the HOSTS menu option on the left menu of the main Termius window.
*   In the hosts list you should see your server. Double-click on it. If all is well, you should be at the servers’ command line.

### More Topics In Command Line

*   [Advanced Backups](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [Alias Domains](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
*   [Server Configuration Files](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-configuration-files/)
*   [View Services Using a Port](https://web.archive.org/web/20240529145252/https://wpclouddeploy.com/documentation/wpcloud-deploy/view-services-using-a-port/)
