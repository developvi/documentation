---
title: "PHP 5.6-7.0-7.1-7.2 & 7.3 Notes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: PHP 5.6-7.0-7.1-7.2 & 7.3 Notes
  parent: 01-cloud-deploy-core
  order: 16
---
# PHP 5.6, 7.0, 7.1, 7.2 & 7.3 Notes

Starting in version 5.3.9 of DevelopVIDeploy, the following versions of PHP are no longer installed or supported on NGINX:

*   PHP 5.6
*   PHP 7.0
*   PHP 7.1
*   PHP 7.2
*   PHP 7.3

Existing NGINX servers will continue to run these versions but if you make changes to any of the following extended functions, support will be removed for the versions listed above:

*   Monit – Changing Monit configuration will remove references to old PHP versions.
*   Netdata – Changing Netdata configuration will remove references to old PHP versions.
*   FileGator
*   Multi-tenancy – Any changes to Multi-tenancy configuration will install new scripts that remove all references and updates to old PHP versions.
*   Git Control – Any changes to GIT configuration will install new scripts that remove all references and updates to old PHP versions.

You will continue to be able to switch the PHP versions for sites that are installed on older NGINX servers.

OpenLiteSpeed servers never supported these versions so there are no historical issues to handle on servers running OpenLiteSpeed.

- - -

## Installing Unsupported Versions

- - -

We understand that you might sometimes need to migrate a WP site that only runs on an older PHP version. Thus, you will be able to install an older PHP version under the UPGRADES tab for a server.

However, most extended functionality will not be available. For example – Monit & Netdata will not monitor these versions and Multi-tenant & Git will no longer attempt to update critical configuration files related to these versions.

To see the status of an older PHP version that you just installed, please click on the REFRESH PHP SERVICES STATUS at the bottom of the SERVICES tab.
