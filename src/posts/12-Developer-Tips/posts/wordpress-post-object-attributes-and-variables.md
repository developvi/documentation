---
title: "WordPress POST Object Attributes and Variables"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: WordPress POST Object Attributes and Variables
  parent: 12-Developer-Tips
  order: 3
---
Do you find yourself constantly Googling the attributes of the WordPress Post Object?

Is it **$post->title** or **$post->post\_title**?

Why does **$post->id** return nothing? Oh, right, because it’s one of the attributes that’s capitalized so it should be **$post->ID**.

Well, bookmark this link and search no longer:

public 'ID' => int
public 'post\_author' => string
public 'post\_date' => string
public 'post\_date\_gmt' => string
public 'post\_content' => string
public 'post\_title' => string
public 'post\_excerpt' => string
public 'post\_status' => string
public 'comment\_status' => string
public 'ping\_status' => string
public 'post\_password' => string
public 'post\_name' => string
public 'to\_ping' => string
public 'pinged' => string
public 'post\_modified' => string
public 'post\_modified\_gmt' => string
public 'post\_content\_filtered' => string
public 'post\_parent' => int
public 'guid' => string
public 'menu\_order' => int
public 'post\_type' => string
public 'post\_mime\_type' => string
public 'comment\_count' => string
public 'filter' => string

## References

[WordPress Documentation on the WP\_POST object](https://web.archive.org/web/20240420015625/https://developer.wordpress.org/reference/classes/wp_post/) – you’ll need to dig into the code shown there. Not quite sure why they didn’t list these fields out there. But that’s WP docs for you.

- - -

### More Topics In Articles

*   [A Guide to SPF, DMARC & DKIM for WordPress](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/a-guide-to-spf-dmarc-dkim-for-wordpress/)
*   [Our Release Cycle: Fast Ring & Slow Ring Releases](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/our-release-cycle-fast-ring-slow-ring-releases/)
*   [Sizing Your WordPress Servers](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/sizing-your-wordpress-servers/)
*   [Deployment Options For DVI](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/deployment-options-for-wpcd/)
*   [Add Your Existing SSH Key To A Root User Account](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/add-your-existing-ssh-to-a-root-user-account/)
*   [All About WP Crons](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/all-about-wp-crons/)
*   [Setup Low Disk Space Alerts](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/setup-low-disk-space-alerts/)
*   [Identify The Largest Files In The WordPress Uploads Folder](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-files-in-the-wordpress-uploads-folder/)
*   [Identify The Largest Sites On Your Server](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-sites-on-your-server/)
*   [Identify The Largest Backups On Your Server](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/identify-the-largest-backups-on-your-server/)
*   [SSL Rate Limits](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/ssl-rate-limits/)
*   [Unable To Create Files (Even With Available Diskspace)](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/unable-to-create-files-even-with-available-diskspace/)
*   [Managing Linux Updates](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/managing-linux-updates/)
*   [How To Lock A Linux User](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/how-to-lock-a-linux-user/)
*   [All About Ubuntu LTS Versions](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/all-about-ubuntu-lts-versions/)
*   [Rapid Reset HTTP/2 & DevelopVIDeploy](https://web.archive.org/web/20240420015625/https://wpclouddeploy.com/documentation/articles-parent/rapid-reset-http-2-wpclouddeploy/)
