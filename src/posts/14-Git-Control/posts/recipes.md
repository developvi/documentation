---
title: "Recipes"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Recipes
  parent: 14-Git-Control
  order: 6
---
## New WP Site with Blank Repo

If you have a new WordPress install on DVI but you don’t have an associated repository yet and you don’t plan on using a local development environment, how can you use the DVI Git Integration?

In this case you would do the following:

*   Go to your Git provider and create a blank repository.
*   Add at least one file to it (eg: dummy.txt) – on Github you can do that from inside your browser in their repo area. The reason for this file is to create the initial git tree – without it there’s no initial tree (.i.e., no starting point.)
*   Initialize the DVI site with GIT (see **Setting Up Two-Way Syncing** in our [Advanced Git](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/advanced-git-two-way-syncing/) documentation) to link it to the new blank repository.

- - -

## Track Just A Single Plugin

Let’s say you only have one or two plugins you want to keep under git control – how would you go about doing that?

The key here is the _.gitignore_ file.

In there you would add the following at the top:

\# Ignore everything
\*

# Except the files in the my-plugin folder
!/wp-content/plugins/my-plugin/
!/wp-content/plugins/my-plugin/\*\*

This works because the first line \* ignores all files, and the next two lines, **!/wp-content/plugins/my-plugin/** _and_ **!/wp-content/plugins/my-plugin/\*\*** un-ignore the **my-plugin** folder and all the files inside it.

Then, you would initialize the site with your git repo containing this file.

When you use our **GIT SYNC** process, it will only sync the plugin files you’re interested in from the current branch.

Note: With something like this, you do NOT want to ever use the **FETCH EXISTING TAG (VERSION) FROM REPO** or **FETCH AND APPLY TAG (VERSION)** actions. So please be careful with those.

- - -

### More Topics In Git Control

*   [Git Control](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/)
*   [Introduction To Git Integration](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/)
*   [Install Git On A Server](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/install-git-on-a-server/)
*   [Git Push-To-Deploy](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/git-push-to-deploy/)
*   [File Exclusions](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/file-exclusions/)
*   [Advanced: (Git) Two-way Syncing](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/advanced-git-two-way-syncing/)
*   [How Do Git Webhooks Work?](https://web.archive.org/web/20240304160039/https://wpclouddeploy.com/documentation/git-control/how-do-git-webhooks-work/)
