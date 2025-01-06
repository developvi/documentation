---
title: "Advanced (Git) Two-way Syncing"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Advanced (Git) Two-way Syncing
  parent: 14-Git-Control
  order: 5
---
## Introduction

DevelopVIDeploy includes the ability to push changes from servers back to your central (remote) repository. While this might sound strange, there are many instances where this can be quite useful.

However, as we illustrated in our [Git Introduction](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/) section, using this ability can easily cause conflicts.

Still, sometimes the advantages outweigh the drawbacks.

One simple use-case is staging sites.

Many professional developers employ a DEV → STAGING → PRODUCTION workflow.

Once you are at the STAGING point of your workflow, it is typical that a lot of troubleshooting and changes might occur directly on the Staging server. In this case it would be quite useful to push those changes back to the repo (maybe on a different branch) instead of trying to manually copy them all back into the local DEV environment.

In this case, your process on a flow-chart might look something like this:

[![](https://web.archive.org/web/20240529150854im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-07.png)](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-single-developer-workflow-07.png)

Another use-case is when running a WordPress SaaS. In this case most development of template sites will occur on a quasi-production server. Pushing and tracking those changes back up to a central (remote) repo is quite useful. And being able to quickly rollback to points in time or deploy different versions can be a lifesaver.

## Setting Up Two-Way Syncing

In git terms, two-way syncing is about using _git init_ to create a local repository on the server for the site and linking that repository back up to your central (remote) one. To do this:

*   Navigate to the **GIT** tab for your site
*   Fill out the requested fields and click the **INITIALIZE GIT ON THIS SITE** button.

[![](https://web.archive.org/web/20240529150854im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-install-git-on-site-03.png)](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-install-git-on-site-03.png)

When the operation completes, the page will refresh and you’ll see a number of new sections:

*   GIT SYNC
*   GIT CHECKOUT BRANCH or TAG
*   GIT CREATE BRANCH
*   GIT CREATE NEW TAG (VERSION)
*   FETCH EXISTING TAG (VERSION) FROM REPO
*   FETCH AND APPLY TAG (VERSION)

We’ll discuss each option in their own sections below.

[![](https://web.archive.org/web/20240529150854im_/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-install-git-on-site-04.png)](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/wp-content/uploads/2022/12/dvi-git-integration-install-git-on-site-04.png)

- - -

- - -

# GIT SYNC

This just brings your site and the current branch up-to-date with the central (remote) repo. It does the following in order:

*   Commits your changes (if any)
*   Pulls changes from the remote and merges them
*   Pushes everything back up to the central (remote) repo

Notice that this operation is on the CURRENT branch. In the image above you can see the current branch (as we know it) is displayed in the green boxes.

- - -

## GIT CHECKOUT BRANCH or TAG

This operation checks out a different branch from the central (remote) repo. All your site files will be switched to match the new branch.

- - -

## GIT CREATE BRANCH

This creates a new branch (using one of the existing branches as a base) and checks it out.

All subsequent changes to the files on the server will be applied to this new branch.

Using the SYNC option mentioned earlier will push changes to the new branch, not the original branch

- - -

## GIT CREATE NEW TAG (VERSION)

A git tag can be thought of as a label. You’re able to navigate back to that label any time you want. In many cases it is used to label versions.

In DevelopVIDeploy, when you create a new git tag, we automatically create a new folder with a copy of all the files in that tag. This folder is located here:

/var/www/yourdomain/versions/tag

Tags created elsewhere (eg: on someone else’s machine or your local dev machine) will not have a versions folder unless you FETCH it (see the next section)

- - -

## FETCH EXISTING TAG (VERSION) FROM REPO

This operation will fetch the files for the tag from the central (remote) git repository and make a copy in the versions folder mentioned earlier.

This is useful if a tag was created elsewhere and DVI knows nothing about it. This operation makes it aware of that new tag/version.

- - -

## FETCH AND APPLY TAG (VERSION)

This option allows you to get a tag and then replace your site with files associated with that tag.

A few things to note about this:

*   Your current branch can believe that the files have changed and, if you commit them, will become the latest version for the branch. This is a great way to corrupt your main branch. If you need to commit, create a new branch first!
*   The PLUGINS, THEMES & MU-PLUGINS folder will be exact copies. This means that files that do not exist in the tag in these folders will be removed.
*   Other files that exist in the site but not in the tag will remain.

This is probably not an operation that you want to use on a regular basis. BUT, it can be quite useful at times.

- - -

## Troubleshooting

### Conflicts with INITIALIZE GIT ON THIS SITE button

When attempting to initialize GIT for a site, it’s possible you might run into conflicts. If your REPO is the source of truth for you, then you can use the **CLONE WITHOUT INIT** button to copy all the repo files to the site first. Then retry the **INITIALIZE GIT ON THIS SITE** button.

### More Topics In Git Control

*   [Git Control](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/)
*   [Introduction To Git Integration](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/)
*   [Install Git On A Server](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/install-git-on-a-server/)
*   [Git Push-To-Deploy](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/git-push-to-deploy/)
*   [File Exclusions](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/file-exclusions/)
*   [Recipes](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/recipes/)
*   [How Do Git Webhooks Work?](https://web.archive.org/web/20240529150854/https://wpclouddeploy.com/documentation/git-control/how-do-git-webhooks-work/)
