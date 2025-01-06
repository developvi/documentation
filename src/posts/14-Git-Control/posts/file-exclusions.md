---
title: "File Exclusions"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: File Exclusions
  parent: 14-Git-Control
  order: 4
---
Whenever we update the files for a site, certain files will be excluded. Which files are excluded depends on the method used to update the site files.

There are SIX ways to update the files for a site using git:

## 1\. Push To Deploy + **COPY CHANGES TO SITE**

For push-to-deploy with the **COPY CHANGES TO SITE** option, all files in the repository are copied to the site. Then, we do a two way sync of the _plugins_, _themes_ and _mu-plugins_ folders so that the files in the repository and the files in those folders are mirror images.

For all other folders, files that are in the site but not in the repository remain in the site.

- - -

## 2\. Push To Deploy + **CHECKOUT**

For push-to-deploy with the **CHECKOUT** option, all files in the repo are synced with the site. In this case, file exclusions are handled using the contents of .gitignore.

- - -

## 3\. Git Init

When we initialize a site with a Git Repo and sync it to your central (remote) repository, we automatically update the .gitignore file with some of our own, non-negotiable file exclusions:

*   wp-config.php
*   logs/
*   filemanager/
*   phpmyadmin/
*   wp-content/debug.log
*   wp-content/downloads
*   wp-conent/updraft
*   \*.log
*   \*.env
*   \*.env.\*

While we say “non-negotiable”, you can still use post-processing scripts to add your own or remove ours.

- - -

## 4\. GIT Sync

All files in the repo are synced using git with the site.

File exclusions are handled using the contents of .gitignore.

- - -

## 5\. GIT Checkout Branch or Tag

All files in the repo are synced using git with the site.

File exclusions are handled using the contents of .gitignore.

- - -

## 6\. Fetch and Apply Tag

All files in the repository are copied to the site. Then, we do a two way sync of the plugins, themes and mu-plugins folders so that the files in the repository and the files in those folders are mirror images.

For all other folders, files that are in the site but not in the repository remain in the site.

- - -

### More Topics In Git Control

*   [Git Control](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/)
*   [Introduction To Git Integration](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/introduction-to-git-integration/)
*   [Install Git On A Server](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/install-git-on-a-server/)
*   [Git Push-To-Deploy](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/git-push-to-deploy/)
*   [Advanced: (Git) Two-way Syncing](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/advanced-git-two-way-syncing/)
*   [Recipes](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/recipes/)
*   [How Do Git Webhooks Work?](https://web.archive.org/web/20231001084606/https://wpclouddeploy.com/documentation/git-control/how-do-git-webhooks-work/)
