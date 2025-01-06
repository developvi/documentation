---
title: "REST API Introduction"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: REST API Introduction
  parent: 11-Rest-Api
  order: 1
---
The DevelopVIDeploy REST API is an ongoing project that will eventually consist of several hundred end points.

The first few endpoints will be production-ready starting with DVI Version 4.14.0.

The REST API uses the standard http verbs:

*   GET: List things such as servers and sites
*   PUT: Change things such as toggle SSL
*   DELETE: Delete things such as servers and sites
*   POST: Create things.

The API is protected by basic HTTP authentication.

You can create HTTP Authentication credentials using the WordPress APPLICATION PASSWORDS function. The RESTAPI will only allow users with the the ADMIN or DVIAdmin roles. All other users will get an authentication error.

Documentation on all endpoints is located here: [DVI REST API Endpoints](https://web.archive.org/web/20240529144652/https://smiinc.stoplight.io/docs/wpclouddeploy/YXBpOjI1MDMwOTYz-wp-cloud-deploy-core-rest-api)

The current endpoints allow you to create new servers and sites, delete those servers and sites, list servers and sites, toggle SSL and clone and change domain for a site.

[Read the full release article](https://web.archive.org/web/20240529144652/https://wpclouddeploy.com/introducing-the-wpclouddeploy-rest-api/)

## Enabling The REST API

The API is disabled by default. You need to explicitly turn it on before you can use it.

*   Navigate to WpCloudDeploy->SETTINGS->APP:WORDPRESS SETTINGS->REST API
*   Activate the checkbox
*   Click the SAVE SETTINGS button at the bottom of the screen.

## Technical Support

The DevelopVIDeploy REST API is available to everyone including Core subscribers and Github users. However, support is only available to **All Access** subscribers and **Lifetime** license holders.

**Technical support is limited to bug reports only.**

Because the REST API is, by definition, a tool to be used by developers, we are unable to offer free support beyond handling bug reports or suggestions for improving documentation. Otherwise we’d be spending an enormous amount of time just debugging customized code for free.

However, a Developer Support contract is available for purchase that will allow for more in-depth consultative support. Just contact us and we’ll create one for you.

## Example Application

Below are some screen shots from a no-code application (i.e.: an application that is not WordPress) that uses the REST API. This is a sample application that we have created to stress-test the endpoints.

[![](https://web.archive.org/web/20240529144652im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-servers-list-01.png)](https://web.archive.org/web/20240529144652/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-servers-list-01.png)

[![](https://web.archive.org/web/20240529144652im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-sites-list-01.png)](https://web.archive.org/web/20240529144652/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-sites-list-01.png)

[![](https://web.archive.org/web/20240529144652im_/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-add-site-01.png)](https://web.archive.org/web/20240529144652/https://wpclouddeploy.com/wp-content/uploads/2022/01/wpcd-rest-api-add-site-01.png)

- - -

## Curl Examples

### Create A Server

curl --request POST \\
https://**yourwpcddomain.com**/wp-json/wpcd/v1/servers \\
--user "**wpcdadmin:wpcdadminpass**" \\
--header 'Content-Type: multipart/form-data' \\
-F "name=\\"test099\\";type=application/json" \\
-F "provider=\\"digital-ocean\\";type=application/json" \\
-F "region=\\"nyc3\\";type=application/json" \\
-F "size=\\"s-1vcpu-1gb\\";type=application/json" \\
-F "author\_email=\\"**[\[email protected\]](/web/20240529144652/https://wpclouddeploy.com/cdn-cgi/l/email-protection)**\\";type=application/json"

Notice that the data is being sent as multipart form but that all the fields are formatted as json.

### Delete A Server

curl --request DELETE https://**yourwpcddomain.com**/wp-json/wpcd/v1/servers/116 \\
--user "**wpcdadmin:wpcdadminpass**"

This deletes server with post id 116.

### Get Status of Long Running Task

curl https://**yourwpcddomain.com**/wp-json/wpcd/v1/tasks/117 \\
--user "**wpcdadmin:wpcdadminpass**"

This will get the status of task with ID 117. This id was given to us from the CREATE A SERVER request.

- - -
