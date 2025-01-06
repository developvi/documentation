---
title: "microsoft-azure-provider-introduction-installation-configuration-guide"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: microsoft-azure-provider-introduction-installation-configuration-guide
  parent: Multi-Cloud Bundle
  order: 11
---
## Installing the Microsoft Azure Provider

The Microsoft Azure provider is just a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

## Prerequisites For Using the Microsoft Azure Provider

Connecting to Microsoft Azure and automatically creating servers requires a lot more moving parts to be synchronized than simpler providers such as DigitalOcean and Linode. In particular:

*   There is a lengthy process for obtaining your credentials – Microsoft does not make this easy. Read the section later in this document titled “Obtaining Azure Credentials”. You will need the following three components of your credentials:
    1.  App ID
    2.  App Password
    3.  App Tenant
*   The credentials must be able to access the Azure SUBSCRIPTIONS endpoint (https://management.azure.com/subscriptions) which is usually not included by default when you generate credentials.
*   You must make sure you create an SSH key pair in the region where you will be building your servers. Each region will need their own key-pair. If you are not familiar with creating or uploading key-pairs using the Azure Portal please see the section below titled “Uploading SSH Keys to Azure”.

- - -

## Configuring the Microsoft Azure Provider

First, you must make sure you create an SSH key pair to the region where you will be building your servers. Each region will need at least one key-pair.

The Azure provider then needs connection and security information before it can be used. You can provide this information under WPCLOUD DEPLOY->SETTINGS->CLOUD PROVIDERS->AZURE. There are several steps to this process – please follow along very CAREFULLY!

*   Enter your **APP ID**, **APP PASSWORD** and **APP TENANT ID**
*   Click the **SAVE** button
*   Click the **SAVE** button AGAIN
*   If all is correct with your credentials, two new fields will appear – **SUBSCRIPTION** and **REGION**. If these fields do not appear then it means that something is wrong with one or more of the three components of your credentials. If you do see these fields then you can proceed to the next step.
*   Choose a SUBSCRIPTION
*   Click the **SAVE** button
*   Click the **SAVE** button AGAIN
*   Choose a REGION
*   Click the **SAVE** button
*   Click the **SAVE** button AGAIN
*   At this point you should see a list of your public keys from your Azure account. If you do not see your keys in this list, use the CLEAR CACHE button at the bottom of the screen to force a data refresh.
*   Select a key from the **PUBLIC SSH KEY** drop-down.
*   Enter your private key that correspond to the public key
*   Click the **SAVE** button
*   Click the **SAVE** button again.

- - -

## Using Multiple Regions

The basic Microsoft Azure provider can only be used in one region. In order to use it in multiple regions, you need to install the [VIRTUAL PROVIDER add-on](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/downloads/virtual-cloud-provider/). Once that has been installed, you can create a virtual provider for each region – learn more in the [Virtual Provider documentation](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/).

- - -

## Obtaining Azure Credentials: Command Line (Recommended)

Before you can get started, you must get a set of credentials from your Azure portal. These credentials are:

*   App ID
*   App Password
*   App Tenant

**Steps:**

*   Log into the Azure Portal
*   Access the CLOUD SHELL using the cloudshell icon (usually in the top right of the portal). If asked about shell type, choose _powershell_.
*   Run this command: **az account show**
*   In the result will be the name of the subscription. Copy that name to the clipboard. We will use it in the next command.
*   Run this command: **az account set –subscription “subscription name”** where “subscription name” is the name of the subscription you got in the first command.
*   Now, run this command to create an app inside the subscription: **az ad sp create-for-rbac -n “your-app-name” –years 50** where “your-app-name” is the name of your application such as “dvi01”. If you get an error about **–years** not being recognized, drop that part of the command.
*   If everything works well you will see output with the three items you need: APP ID, PASSWORD & TENANT. Make sure you copy them to a safe place so you can use them later. Especially make sure you copy the password – you will not be able to see it in the Azure Portal.

- - -

## Obtaining Azure Credentials: Azure Portal (Not Recommended)

If you don’t want to use the command line, we’re working on figuring out the proper steps for doing it visually in the Azure Portal. But, we haven’t quite gotten it right yet.

The items needed are not all located in the same place in the portal. The official Microsoft documentation for them is located here: [https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal](https://web.archive.org/web/20240420013042/https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal)

Unfortunately, that documentation is not exactly the easiest to understand – Microsoft wanders all over the place in it.

The following are the basic steps as far as we can tell. **Unfortunately at least one key step is missing and we’re in contact with Microsoft about it:**

*   Log into your Azure portal as the Admin for your organization
*   Click on the **Azure Active Directory** item – on this screen you will see your TENANT ID.
*   Click on the **App Registrations** option in the left menu bar to create a new application
*   Click on the **New Registration** option at the top of the screen
*   Give the app a name and then click the REGISTER button at the bottom of the screen
*   You should now be inside the app screen. The APPLICATION ID should be shown at the top of the screen.
*   Click on the **Certificates and Secrets** option in the left menu bar
*   Click on **New Client Secret** (about halfway down the page) to create a new secret – this will be your APP PASSWORD

- - -

## Uploading SSH Keys to Azure

To create or upload SSH keys to Azure, follow the instructions in this Microsoft document: [https://docs.microsoft.com/en-us/azure/virtual-machines/ssh-keys-portal.](https://web.archive.org/web/20240420013042/https://docs.microsoft.com/en-us/azure/virtual-machines/ssh-keys-portal)

As mentioned above, each region you use will need their own key-pair.

- - -

## Azure Limits

If you cannot create servers, it could be that you’ve bumped up against an azure limit. For example:

*   You might not be allowed more than 10 public IP addresses for a subscription in region – this means you can’t have more than 10 public web servers in the region unless you get Microsoft to raise the limit. Check your account to make sure you don’t have stray public addresses and, if you do have 10 or more that are needed, check with Microsoft to get your limits raised.
*   If you create a server and then delete it, the IP address might remain behind which will contribute to your limits.

- - -

## Limitations

### Server Sync

Server Sync cannot be used on Azure servers – neither as source nor destination.

### Site Sync

The function to copy a site to a new server will not work with this provider.

### Deleting A Site

When deleting a site, the option to also delete all local backups will not work with this provider.

- - -

## Important Notes

### SSH Logins

Azure, like AWS and some other cloud services, do not allow ssh logins using the “root” user. So we have setup a user called _dviadmin_ as the default admin user. When logging in with your ssh client, make sure your user name is set to _dviadmin_ instead of “root”.

### DVI Feature Compatibility

Because we cannot use the root login, the following DVI features will not work:

*   Server Sync / Failover

### Deleting A Server

It is possible that server resources such as disks, IP address and resource groups might not be deleted in Azure even though the VM has been deleted in DVI. This is because Azure will not automatically delete those items when a server is deleted. And it takes Azure a long time to delete a server which exceeds the PHP script execution time. Therefore, whenever you delete a server in DVI you should double-check that it has been deleted in Azure.

We’ve attempted to mitigate this issue a bit by scheduling a CRON process to clean up undeleted items shortly after deleting a server. But there’s no guarantee that we will get everything – so always double-check your Azure console to make sure that all items are deleted – you do not want to be surprised with a bill for items you thought you deleted!

### Server Names

Azure requires your server names to be unique. So, we will be adding a random 5 character string to the end of every server name you specify to avoid inadvertent duplicates. This means that if you try to create a server with the name “MYNEWSERVER” we will convert it into something like “MYNEWSERVER-axytz”.

### Default Disk Size

All servers, regardless of number of CPUs, will be provisioned with 50 GB of disk space.

Azure has a weird issue with disk sizes – it sometimes reports the disk as being full until you restart the server.

- - -

## ARM Processor Support

This provider includes experimental support for ARM instances. While ARM VMs are supposed to be lower cost, the way Azure has configured their VMs seem to negate that cost advantage. Still, for certain workload profiles, there might be some cost savings here.

We have tested basic **NGINX** & **OPENLITESPEED** functionality such as deploying the server, sites and SSL. But have not certified 3rd party software such as MONIT and MALDET. Thus, this is not something you should run in production if you require 3rd party software support; but they might make good development or staging servers if you like playing on the bleeding edge of things.

They’re also great instances to use if all you are doing is creating sites that use just the basic WP functions without any of the advanced DVI features. i.e.:

*   Install Site
*   Enable/Disable SSL
*   Enable/Disable CACHE
*   Backup/Restore
*   Site Tweaks
*   etc.

Almost anything that only uses PHP should work but anything that requires a binary (most 3rd party software) have not been certified.

- - -

### More Topics In Multicloud

*   [All About Cloud Server Providers](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/all-about-cloud-server-providers/)
*   [Alibaba ECS Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/alibaba-ecs-provider-introduction-installation-configuration-guide/)
*   [DigitalOcean Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/digital-ocean-provider-introduction-installation-configuration-guide/)
*   [EC2 Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/ec2-provider/)
*   [Exoscale Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/exoscale-provider-introduction-installation-configuration-guide/)
*   [Linode Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/linode-provider-introduction-installation-configuration-guide/)
*   [UpCloud Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/upcloud-provider-introduction-installation-configuration-guide/)
*   [Hetzner Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/hetzner-provider-introduction-installation-configuration-guide/)
*   [Vultr Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/vultr-provider-introduction-installation-configuration-guide/)
*   [Google Compute Engine: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/google-compute-engine-introduction-installation-configuration-guide/)
*   [Lightsail Provider: Introduction, Installation & Configuration Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/lightsail-provider-introduction-installation-configuration-guide/)
*   [Proxmox Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/proxmox-private-cloud-provider-introduction-configuration-installation-guide/)
*   [OpenStack Private Cloud Provider: Introduction, Configuration & Installation Guide](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/openstack-private-cloud-provider-introduction-configuration-installation-guide/)
*   [Changing SSH Keys For A Cloud Provider](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/changing-ssh-keys-in-cloud-provider-settings/)
*   [Custom Images](https://web.archive.org/web/20240420013042/https://wpclouddeploy.com/documentation/cloud-providers/custom-images/)
