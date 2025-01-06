---
title: "introduction-to-git-integration"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: introduction-to-git-integration
  parent: 14-Git-Control
  order: 1
---
## Introduction

GIT is a distributed version control system that allow multiple users to simultaneously make changes to files and commit them to a central repository. Most conflicts are intelligently handled but commits will be rejected if the git server cannot figure out how to merge changes from multiples sources.

This flexibility is also its greatest drawback and lead to a LOT of confusion among developers.

Still, DevelopVIDeploy supports this multi-direction, multi-user editing. Though, for most use-cases it is probably better to use a more linear approach.

A typical individual-developer process might look like this:

## [![](https://web.archive.org/web/20240529161808im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-06.png)](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-06.png)

As you can see, the flow is one way – all changes originate from the developer’s machine.

In this case, there is no need to create a git repository on the server where the site resides. All that is needed is the git credentials for the central (remote) repository.

However, there are other, more advanced workflows that can be used if git is initialized on the production or staging site on the server and linked to the central (remote) repository.

For example:

[![](https://web.archive.org/web/20240529161808im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-03.png)](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-03.png)

ummm…you might be thinking that this looks simpler because there are less blocks on here compared to the last image – so why are we saying this is more complex?

The answer is simple – you’re pushing files / changes in both directions and to multiple machines.

For example, if you add or update plugins & themes on the production or staging server, they can be pushed to the central (remote) repository and then further pushed down to the developer’s local environment.

An even more advanced case is this:

[![](https://web.archive.org/web/20240529161808im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-02.png)](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-02.png)

[![](https://web.archive.org/web/20240529161808im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-04.png)](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-04.png)

Notice that many of the arrows point in BOTH directions. In these cases, file changes:

*   Flow both ways between a developer’s local environment and the remote repo (eg; on Github).
*   Flow both ways between multiple developers and the remote repo.
*   Flow both ways between developers and the production (or staging) website.
*   The production (or staging) website can be updated at any time by the webhook trigger when developers (or any other source) push changes to the remote repo.

- - -

## About The Database

Git is all about files. Usually plugins and themes and, maybe, the core WordPress files.

There is no version control or syncing of the data in the database.

Changes to the database as you upgrade your site needs to be handled with a custom plugin that deletes, updates and adds data.

- - -

## Activating Git Options

Git Control is a premium option offered only as a combined software + services product. The software (plugin) is not available without the services component.

The software is provided as a regular WordPress plugin – upload and activate it from the WordPress PLUGINS screen.

Once activated you will see a few new options:

*   A new GIT tab in your global SETTINGS area under WpCloudDeploy → APP: WORDPRESS SETTINGS → GIT
*   A new GIT tab under each server
*   A new GIT tab under each site (if you activated GIT for a server).

- - -

## Basic Setup

The easiest way to connect your servers and sites to GIT is to setup global GIT options under WpCloudDeploy → APP: WORDPRESS SETTINGS → GIT

There you can add a few settings that will be used by all your servers and sites.

*   Email Address used for your Git Provider account
*   The display name that will be used by Git
*   The user name for your Git Provider account
*   The API token created in your Git Provider account
*   A primary branch – usually ‘master’ or ‘main’

Some advanced options used for two-way syncing include:

*   pre-processing and post-processing scripts
*   gitignore settings

[![](https://web.archive.org/web/20240529161808im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-git-setup-01.png)](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-git-setup-01.png)

- - -

## Supported Git Providers

We only support one provider at this time:

*   Github

- - -

## Credential Hierarchy

If you’re using the same set of credentials (and other related settings) for all your sites, you only have to set them up in the GLOBAL settings area. Sites will automatically pull them from there when first initialized with git.

You can also set up server-specific GIT credentials in the server screen. Sites on the server will pull from those settings first before looking to the global settings for values.

Finally, you can give each site its own unique set of credentials. This is useful if you’re managing multiple git repos for various customers for sites on a shared server (eg: a development server.)

- - -

## Support Policy

_The GIT module is only available as part of a [services or upgraded support package](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/downloads/git-control/). We fully expect that there will be lots of questions related to how best to apply this module to your use-case and goals. Since that kind of in-depth, organization-specific support is not something we can reasonably provide for free in our ALL ACCESS bundle support, the only way to offer this feature is by making it part of a services or upgraded support contract._

_However, the code is opensource on GITHUB and experienced ALL ACCESS developers can use it as they see fit. Just keep in mind that this is not an install-and-go feature – it does require at least a smidgen of developer level work (hence the necessity for the services and support package)._

_This is not your standard GIT integration with only web-hooks. It is a fully distributed bi-directional integration that takes full advantage of the decentralized and distributed nature of GIT._

_Software developers can grab the code in our [github repository](https://web.archive.org/web/20240529161808/https://github.com/wpclouddeploy/wp-cloud-deploy)._

- - -

### More Topics In Git Control

*   [Git Control](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/)
*   [Install Git On A Server](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/install-git-on-a-server/)
*   [Git Push-To-Deploy](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/git-push-to-deploy/)
*   [File Exclusions](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/file-exclusions/)
*   [Advanced: (Git) Two-way Syncing](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/advanced-git-two-way-syncing/)
*   [Recipes](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/recipes/)
*   [How Do Git Webhooks Work?](https://web.archive.org/web/20240529161808/https://wpclouddeploy.com/documentation/git-control/how-do-git-webhooks-work/)
