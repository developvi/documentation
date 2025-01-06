---
title: "How To Generate An SSH Key-Pair With Termius"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Generate An SSH Key-Pair With Termius
  parent: 09-Command-Line
  order: 3
---
DevelopVIDeploy uses ssh key-pairs to log into servers – it does not use passwords. If you do not already have a keypair, we have [instructions for creating one using the command line](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/how-to-generate-an-ssh-key-pair/).

However, there is an alternative – one that has the side-effect of also installing a very cool SSH client.

It involves the use of a product named [TERMIUS](https://web.archive.org/web/20240529152948/https://termius.com/).

Termius is probably the most user-friendly SSH client we’ve seen. And in a recent update it added the ability to create an ssh key-pair without using the command line.

To get started, you will need to download and install it. Download links for the various operating systems are usually in the footer of the Termius website.

The basic package is free and comes with a trial of their premium features.

## Generating A Key-pair

1\. Click the “Gear” button on the upper left side of the Termius screen:

[![](https://web.archive.org/web/20240529152948im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-02.png)](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-02.png)

2\. Click the KEYCHAIN menu option in the popup screen

[![](https://web.archive.org/web/20240529152948im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-04.png)](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-04.png)

3\. At the top of the KEYCHAIN screen, click the NEW KEY button and then click GENERATE NEW KEY from the drop-down:

[![](https://web.archive.org/web/20240529152948im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-06.png)](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-06.png)

4\. In the NEW KEY screen: 1.) generate a 4096 bit RSA key or an ED25519 key. 2.) Do NOT give it a password but do give it LABEL. 3.) Then click the GENERATE & SAVE button.

[![](https://web.archive.org/web/20240529152948im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-08-1.png)](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-08-1.png)

5\. Upload the PUBLIC KEY text to your cloud provider. Add the PRIVATE KEY text to the DVI settings area for the provider.

[![](https://web.archive.org/web/20240529152948im_/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-10.png)](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/wp-content/uploads/2022/07/wpcd-termius-10.png)

### More Topics In Command Line

*   [Advanced Backups](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/)
*   [Alias Domains](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
*   [How To Login To Your Server Via SSH](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-login-to-your-server-via-ssh/)
*   [Server Configuration Files](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-configuration-files/)
*   [View Services Using a Port](https://web.archive.org/web/20240529152948/https://wpclouddeploy.com/documentation/wpcloud-deploy/view-services-using-a-port/)
