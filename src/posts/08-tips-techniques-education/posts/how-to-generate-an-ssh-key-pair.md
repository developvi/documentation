---
title: "how-to-generate-an-ssh-key-pair"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: how-to-generate-an-ssh-key-pair
  parent: 08-tips-techniques-education
  order: 4
---
All of the servers that are linked to our platform need to use SSH keys. Most server providers allow you to add the public portion of the key to your account which will then be added to new servers you create. For those providers you will see a drop-down in our settings screen showing the existing keys you have uploaded and asking you to provide the private key portion.

This document will explain everything you need to know about SSH keypairs including how to properly generate them using the command line.

Note: You can generate them without using the command line – [see our TERMIUS article](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/).

## About SSH Keys

SSH Keys are two text files that consist of your PUBLIC KEY and your PRIVATE KEY. The data in your Public Key is uploaded to your cloud provider while your private key is entered into the DVI configuration screens. Your cloud provider will install your public key into any servers it creates for you. Your private key in DVI will be used to match against the public key when we try to log in to the server.

When you create a public key pair you need to decide a few things:

1.  The strength of the keypair – most operating systems default to 2048 bits but you can increase this size.
2.  The encryption you will use – RSA, an Elliptic Curve or one of the many other options available
3.  The key format for the data stored in the private key file (we also refer to this as the file format but the precise terminology is “key format”). Some common key formats are PKCS1, PKCS8 and OPENSSH. (Your public key will usually be in OPENSSH format regardless of the private key format .)

There are some trade-offs to your key format decision so lets discuss that before we walk you through the process of generating your key pair.

*   If you choose a PKCS1 or PKCS8 key format you can optionally use a password for the private key. However, the password must consist of alpha-numeric characters only.
*   If you choose an OPENSSH key format for your private keys, you CANNOT use a password for it. This is because we use the [PHPSecLib library](https://web.archive.org/web/20240529145619/https://phpseclib.com/docs/publickeys) to handle keys and one of its limitations is lack of support for password protected OpenSSH keys. _Most modern operations will default to creating keys in the OPENSSH format and ask you for a password so this is something you must be aware of when generating keys._

## What If I Have Existing Keys?

You can use your own keys if any of the following is true about your keys:

1.  The private key is in PKCS format without a password
2.  The private key is in PKCS format with a password consisting of only alphanumeric characters
3.  The private key is in OPENSSH format without a password (As mentioned above we use the [PHPSecLib library](https://web.archive.org/web/20240529145619/https://phpseclib.com/docs/publickeys) to handle keys and one of its limitations is lack of support for password protected OpenSSH keys.)

**If you used a MAC or WSL or Ubuntu 20.04 or later to generate your keys and used the ssh-keygen defaults, there is a good chance you ended up with an OPENSSH key format. This means that if you created it with a password you will NOT be able to use it with DVI. You should generate a new pair without the password.**

## Other Recommendations

**We strongly recommend that you use an ssh keypair that is not in use anywhere else. It is good security practice to avoid reusing your keys across different services.**

If you use different cloud providers you should use a different keypair at each of them.

- - -

# How To Generate Keys (Termius)

The easiest way to generate new SSH keys is to use a program called TERMIUS. It has a nice GUI that makes it very simple. We have a separate help document that covers this option:

> [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)

- - -

# How To Generate Keys (Command Line)

This section covers how to generate a new keypair using the command line. Once generated, you will upload the public key portion to your provider’s service and enter the contents of the private portion into our settings screen.

You should save both parts in a safe location!

## What You Will Need

For the purposes of this article you will need access to an ubuntu based machine. If you do not have one already, you can quickly fire up a temporary one on any of the cloud server providers such as DigitalOcean, Linode, Vultr etc. By far the easiest to use is DigitalOcean. (You can also use the Windows Subsystem for Linux (aka WSL) or a MAC.)

Once you’re logged in on the command line, use the ssh-keygen command:

$ ssh-keygen -m pem

This command will generate a 2048 bit key pair in a PKCS key format. You can generate a stronger 4096 key pair by using the _\-b 4096_ flag.

$ ssh-keygen -b 4096 -m pem

After running the command you should see something like this in the output:

_Generating public/private rsa key pair._
_Enter file in which to save the key (/your\_home/.ssh/id\_rsa):_

To avoid overwriting any default existing keys, you should enter an alternate path instead of allowing use of the default .ssh/ folder in your home directory. Entering a name without a path will place the file in your current folder.

After entering a new path, you should see a prompt asking for a password:

_Enter passphrase (empty for no passphrase):_

It’s asking you for a password that will be used to encrypt the private portion of your key pair. You can leave it blank by just hitting the enter key or, of course, enter an alpha-numeric password. (Just make sure you remember the password otherwise the entire keypair will be useless.)

*   Your password should consist of only alpha-numeric characters – no “special” characters should be used.

After the password prompt, your keypair will be generated and placed into the directory you specified. You can download both files from that directory onto your local machine. Add the public portion to your cloud provider’s service.

### Generating Keys on Older Operating Systems

If you’re using an older OS to generate your keys – eg: Ubuntu 18.04, you might get an error using the ‘-m’ parameter shown in the above examples. If that’s the case, just drop it – usually an RSA key in PKCS format will be generated by default:

$ ssh-keygen -b 4096

### Some Important Notes about SSH Keys

The commands we gave you above generates PKCS RSA keys. You can generate OpenSSH formatted keys by dropping the ‘-m’ parameter on newer operating systems which creates OpenSSH formatted keys by default:

$ ssh-keygen -b 4096

These types of keys will work with DVI – as long as you do NOT use a password with them. We use the [PHPSecLib library](https://web.archive.org/web/20240529145619/https://phpseclib.com/docs/publickeys) to handle keys and one of its limitations is lack of support for password protected OpenSSH keys.

- - -

## Related Videos

### How to generate an SSH key-pair in Windows and upload to DigitalOcean, Linode & Vultr

The videos below will help you visualize the process for generating keys. _Please note that the commands you enter must use the ‘-m pem’ parameter to get RSA/PEM keys – this is not shown in the videos since they were recorded before the default ssh-keygen format was changed from RSA/PEM to OpenSSH._

### How to generate an SSH key-pair on a Mac and upload to DigitalOcean, Linode & Vultr

### How to generate an SSH key-pair on Linux and upload to DigitalOcean, Linode & Vultr

## Important Notes

1.  If you add a password to your private key, keep it to letters and numbers only. It reduces the chances that you inadvertently use a special character than means something to the Linux command line.
2.  If you use a MAC or the WSL to generate your keys using just the default parameters, do NOT add a password to the private key.

- - -

## How To Determine The Format Of Your Private Key

Your public key file will almost always start with “ssh-rsa” or “ssh-ed25519” which indicates an OPENSSH format. Eg:

**ssh-rsa** AAAAB3NzaC1yc2EAAAADAQABAAABAQDAejKY/gtRZqjqOLx6ZTEIjAG+
X2KUh0YQOko+FD/jiHMHF25oZWUSqPVz7xQOBmdFn+8bqPnHjzc+fipJDtrA/BX0
9QNM2LRzm98dP/PkyeoFMoZLNf8NrbwLOzZAkTMyeuZYqQRlPrNszglY/AK52Drf
qm2zw7t53Ux6m1btmm4DJcijaEkfkUQHtvyH1VcsDxpuYUk4hayxYeXx2jMwpcY4
JP6yRiAO+BbNjj8d4x7zSWZzEkeqe++EfSvhjXz+uibQFSdeEL8TA22NA7rqYck7
8aEyrhrKkbPydoAShrSofW37FWioX9BrtNHIkX3/nlXbUfc+OUZ2iOWW/CCL

Your private key will usually start with one of the following:

1.  —–BEGIN RSA PRIVATE KEY—–
2.  —–BEGIN PRIVATE KEY—–
3.  —–BEGIN OPENSSH PRIVATE KEY—–

Item 1 is a PKCS1 formatted private key. Item 2 is a PKCS8 formatted private key. Item 3 is an OPEN SSH formatted private key.

If your private key file starts with a line similar to item 3 above, it must NOT have a password associated with it!

- - -

## Add Keys To Your Cloud Providers’ Dashboard

[Add your public key to Digital Ocean](https://web.archive.org/web/20240529145619/https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/to-account/)

[Add your public key to Vultr](https://web.archive.org/web/20240529145619/https://www.vultr.com/news/Pre-load-Your-New-VPS-With-SSH-Keys/)

[Add your public key to UpCloud](https://web.archive.org/web/20240529145619/https://upcloud.com/community/tutorials/managing-ssh-keys/)

## 3rd Party Resources

Here are some useful links to documents about generating SSH keys written by various cloud server providers:

[Install an OPENSSH client on Windows 10](https://web.archive.org/web/20240529145619/https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) – useful if you want to use the command prompt to access a remote machine via SSH.

[Generate key pairs using PuTTY](https://web.archive.org/web/20240529145619/https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/create-with-putty/) – this is useful if you are working on a Windows machine and really don’t want to spin up a temporary cloud server.

[Generating key pairs on MacOS](https://web.archive.org/web/20240529145619/https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/create-with-openssh/)

[Generating and using SSH Keys on Vultr](https://web.archive.org/web/20240529145619/https://www.vultr.com/docs/how-do-i-generate-ssh-keys/)

[More information about key format differences](https://web.archive.org/web/20240529145619/https://www.jhanley.com/security-key-pairs-and-private-public-keys/)

### More Topics In Tips, Techniques & Education.

*   [Increase WordPress Upload Size](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/increase-wordpress-upload-size/)
*   [How To Access The Entire Server via sFTP](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-access-the-entire-server-via-sftp/)
*   [How Do I Limit PHP Workers For Each Subdomain On A Multisite?](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/how-do-i-limit-php-workers-for-each-subdomain-on-a-multisite/)
*   [Considerations For A Large Number Of Sites On A Single Server](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/considerations-for-a-large-number-of-sites-on-a-single-server/)
*   [All The Possible WP-CONFIG.PHP Constants For Core WordPress](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/all-the-possible-wp-config-php-constants-for-core-wordpress/)
*   [Using MIGRATE GURU To Import Sites](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/multitenant/tips-troubleshooting-limitations/using-migrate-guru-to-import-sites/)
*   [Force The Use of WWW On A Website](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/force-the-use-of-www-on-a-website/)
*   [Local & Remote Statuses On Servers](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/local-remote-statuses-on-servers/)
*   [CORS Example: Allow Access to Resources Between www and non-www Domains](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/cors-example-allow-access-to-resources-between-www-and-non-www-domains/)
*   [Import Sites](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/import-sites/)
*   [Transferring Sites Between Servers](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/transferring-sites-between-servers/)
*   [Monit vs Netdata vs Monitorix vs GoAccess](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/monit-vs-netdata-vs-monitorix-vs-goaccess/)
*   [Resolving Common Issues With CloudFlare](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/resolving-common-issues-with-cloudflare/)
*   [View Used Disk Space For A Site](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/view-disk-space-for-a-site/)
*   [Customizing Front-end Styles](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/customizing-front-end-styles/)
*   [How To Generate An SSH Key-Pair With Termius](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/articles-parent/how-to-generate-an-ssh-key-pair-with-termius/)
*   [How To Change Your DNS Server](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/how-to-change-your-dns-server/)
*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Tweaking The Malware Scanner](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/tweaking-the-malware-scanner/)
*   [Handling Low Disk Space Conditions](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/handling-low-disk-space-conditions/)
*   [Useful OpenLiteSpeed Commands](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/useful-openlitespeed-commands/)
*   [Alias Domains](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/alias-domains/)
*   [Custom SSL Certificates](https://web.archive.org/web/20240529145619/https://wpclouddeploy.com/documentation/tips-techniques-education/custom-ssl-certificates/)
