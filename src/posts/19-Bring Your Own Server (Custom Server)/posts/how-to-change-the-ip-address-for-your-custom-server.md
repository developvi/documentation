---
title: "how-to-change-the-ip-address-for-your-custom-server"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: how-to-change-the-ip-address-for-your-custom-server
  parent: Bring Your Own Server (Custom Server)
  order: 2
---
# How To Change The IP Address For Your Custom Server

If the IP Address for your custom server changes, you will need to change it in two locations in DVI.

The first place you need to change it is in the SETTINGS for the cloud provider as follows:

*   Go to the **DevelopVIDeploy** → **SETTINGS** → **CLOUD PROVIDERS** tab
*   Click on the tab for your custom server
*   Change the _IP Address_ field
*   Click the **SAVE SETTINGS** button at the bottom of the screen.

The next place that needs to be updated is the SERVER record itself. To do this, you first need to expose some advanced data entry fields:

*   Go to the **DevelopVIDeploy** → **SETTINGS** → **MISC** tab
*   Scroll down to the **SHOW ADVANCED METABOXES** section
*   Enable the checkbox
*   Click the **SAVE SETTINGS** button at the bottom of the screen.

Then update the SERVER record as follows:

*   Navigate to **DevelopVIDeploy** → **CLOUD SERVERS**
*   Locate and click on your server record
*   Scroll down until you find the **SERVER DETAILS** box
*   Update the _IPv4 ADDRESS_ field (and, if applicable, the _IPv6 ADDRESS_ field)
*   Click the **UPDATE** button in the upper right of the screen.

Finally, disable the ADVANCED METABOXES settings:

*   Go to the **DevelopVIDeploy** → **SETTINGS** → **MISC** tab
*   Scroll down to the **SHOW ADVANCED METABOXES** section
*   Disable the checkbox
*   Click the **SAVE SETTINGS** button at the bottom of the screen.

- - -

### More Topics In Custom Servers

*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420011821/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
