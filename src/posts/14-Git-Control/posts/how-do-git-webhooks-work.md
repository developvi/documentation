---
title: "How Do Git Webhooks Work?"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How Do Git Webhooks Work?
  parent: 14-Git-Control
  order: 7
---
In our Push-to-Deploy documentation we use the term Webhooks. But we didn’t quite explain what they are. Hopefully, if you’re using GIT you already know but we’re including this brief explanation just in case.

Let’s start with this image which shows a typical individual developer Workflow.

[![](https://web.archive.org/web/20240221060644im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-05.png)](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-05.png)

Now let’s walk through the steps in a bit more detail:

*   Files are pushed from your local development environment (or from any other source linked to the repo) up to the central (remote) repository.
*   When files are pushed, your git provider (eg: GitHub) uses the webhook that is configured for the site and sends a payload to the webhook url. The webhook is simply a specially crafted URL with a known json payload.
*   We use the ‘secret’ that is configured as part of the Github webhooks to verify that the payload has not been tampered with.
*   If the payload was triggered by a push to a known branch (configured inside the Push-To-Deploy area), DVI then triggers an action on the server where the site is installed to pull the latest files from that branch

While it might not be fully obvious, one of the things you can do is configure your git provider to send web hook calls to multiple sites.

[![](https://web.archive.org/web/20240221060644im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-08.png)](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-08.png)

In other words, a single push to your main branch can trigger updates on 1, 2, 10 or 25 sites if all those webhooks are configured. Of course, if you actually do this, make sure your DVI server is beefy enough to accept all those incoming connections at once. Otherwise your git provider will just register the webhook call as failed or timeout. (And some providers do have a hard limit on the number of webhooks you are allowed to configure.)

### More Topics In Git Control

*   [Git Control](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/)
*   [Introduction To Git Integration](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/)
*   [Install Git On A Server](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/install-git-on-a-server/)
*   [Git Push-To-Deploy](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/git-push-to-deploy/)
*   [File Exclusions](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/file-exclusions/)
*   [Advanced: (Git) Two-way Syncing](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/advanced-git-two-way-syncing/)
*   [Recipes](https://web.archive.org/web/20240221060644/https://wpclouddeploy.com/documentation/git-control/recipes/)
