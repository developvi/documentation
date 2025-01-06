---
title: "How To Make Edits Directly In Core Files And Not Lose Changes On Upgrades"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: How To Make Edits Directly In Core Files And Not Lose Changes On Upgrades
  parent: 12-Developer-Tips
  order: 5
---
There are times when all you want to do is make a quick modification without having to create a separate plugin and write all the code to tap into DVI’s hook and filters. For example, you might just want to change the default upload file size from 25M to 50M. Literally two characters. But it’s two characters that will get stomped on with every DVI update.

If you’re familiar with the GIT version control system, it is possible to do simple changes like this without completely losing them on every DevelopVIDeploy update.

There are two caveats to this though:

1.  There will be times where an update will step on your changes and you’ll have to remake them in the latest DVI version and
2.  You can no longer use the WordPress automatic update functions.

(Also, this technique works for any plugin or theme where you want to make updates directly to the files.).

The way it works is like this:

1.  Create a personal git repository for the base DVI plugin – eg: V 4.15.0. Let’s call the main branch “MAIN”.
2.  Create a new branch from MAIN – lets call that one “CUSTOM”.
3.  Make your changes in the CUSTOM branch and commit them.

This is your baseline. Zip up the CUSTOM branch and upload to your WP install just like you would any other plugin (or upload via sFTP.)

## Apply DVI Updates

When you need to apply a new DVI update, eg: V 4.16.0, you would do this as follows:

1.  Switch to the MAIN branch.
2.  Replace the files there with the files from new version of DVI.
3.  Commit.
4.  Switch to the CUSTOM branch.
5.  Merge the MAIN branch into the CUSTOM branch.
6.  Commit.

If all goes well, there should be no conflicts during the merge. If this is the case, you can zip up your CUSTOM branch and upload to your WordPress install – it will contain all the latest DVI changes along with your changes.

If you do see conflicts, you’ll need to create a new branch from MAIN (called CUSTOM2 for example) and reapply your changes manually. Or, if you’re an experienced GIT user, you can resolve the conflicts and commit in the CUSTOM branch.

## Visual Tools

If you’re not a command line user, there are many visual GIT tools. The one we use is called SMARTGIT. But you can also do this using just the browser based tools in GITHUB (or BITBUCKET or GITLAB or any other online git service).

## Final Notes

You can also use this technique for all DVI add-ons. Need to change the default deployment parameters for EC2? Or maybe tweak how a WC site is deployed? These kinds of minor changes are perfect for this technique if you’re willing to live with the limitations and caveats we mentioned earlier.

### More Topics In Developer Tips

*   [Using Visual Studio Code With DevelopVIDeploy](https://web.archive.org/web/20240529151024/https://wpclouddeploy.com/documentation/developer-tips/using-visual-studio-code-with-wpclouddeploy/)
*   [How To Remove The DEPLOY A NEW WORDPRESS SERVER Button](https://web.archive.org/web/20240529151024/https://wpclouddeploy.com/documentation/developer-tips/how-to-remove-the-deploy-a-new-wordpress-server-button/)
*   [Add Custom Search Fields To The App (Site) List](https://web.archive.org/web/20240529151024/https://wpclouddeploy.com/documentation/developer-tips/add-custom-search-fields-to-the-app-site-list/)
