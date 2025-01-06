---
title: "Home Page Images"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Home Page Images
  parent: 24-Powertools
  order: 6
---
## Introduction

The Home Page Images feature allow you automatically capture and store an image of the home page for all sites. This image can then be added to the site list.

[![](https://web.archive.org/web/20240420012131im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-home-page-image-02.png)](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-home-page-image-02.png)

We depend on a 3rd party service to capture images so you’ll need to create and setup an account there as described below.

- - -

## Step 1: Setup Your API Keys

We use a service called [htmlcsstoimage.com](https://web.archive.org/web/20240420012131/https://htmlcsstoimage.com/) to capture web page images. If you don’t already have an account there you need to create one before you can use this feature.

Then go to the **DevelopVIDeploy → SETTINGS → APP:WORDPRESS SETTINGS → INTEGRATIONS** tab.

There you can enter the API keys for the _htmlcsstoimage.com_ service.

One of the nice things about this service is all images live there – we do not store the images in the local WordPress MEDIA library.

## Step 2: Enable The Home Page Feature

No additional steps are necessary to enable this feature. If the API keys are present we’ll use them to capture an image for the site once per week.

## Step 3: (Optional) Enable The Home Page Column

If you’d like to see the image in your sites list you need to enable it. You can do this as follows:

*   Navigate to **DevelopVIDeploy→ SETTINGS → APP: WORDPRESS SETTINGS → POWERTOOLS**
*   Scroll down to the **SITE HOMEPAGE IMAGES** section
*   Click the checkbox labeled _Show home page image column for sites?_
*   Click the SAVE button at the bottom of the screen.

If you don’t enable this column you’ll still be able to see the image in the HOME PAGE IMAGE metabox when you go to the site details.

- - -

## Capture An Image On Demand

We capture an image once a week. However, you can capture an image immediately using the HOME PAGE IMAGE metabox.

[![](https://web.archive.org/web/20240420012131im_/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-home-page-image-05.png)](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/wp-content/uploads/2022/04/wpcd-powertools-automatic-home-page-image-05.png)

- - -

## Disable This Feature

If you don’t want to use this feature at all you can disable it as follows:

*   Navigate to **DevelopVIDeploy -> SETTINGS -> APP: WORDPRESS SETTINGS -> POWERTOOLS**
*   Scroll down to the **SITE HOMEPAGE IMAGES** section
*   Click the checkbox labeled _Disable home page images for sites?_
*   Click the SAVE button at the bottom of the screen.

- - -

### More Topics In Powertools

*   [Powertools Introduction](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/powertools-introduction/)
*   [Dashboard](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/dashboard/)
*   [Scheduled Snapshots](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/scheduled-snapshots/)
*   [Netdata Integration](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/netdata-integration/)
*   [Recurring Site Images](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/recurring-site-images/)
*   [Automatic Server Restarts](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/automatic-server-restarts/)
*   [Automatic Backups On A Different Schedule](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/automatic-backups-on-a-different-schedule/)
*   [Run Callbacks More Frequently](https://web.archive.org/web/20240420012131/https://wpclouddeploy.com/documentation/powertools/run-callbacks-more-frequently/)
