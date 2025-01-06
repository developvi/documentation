---
title: "Removing Code & JS Inputs in Beaver Builder"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Removing Code & JS Inputs in Beaver Builder
  parent: 18-Wordpress-Saas
  order: 2
---
When you’re creating a WordPress SaaS you might want to allow your users the use of a page builder such as Beaver Builder.

However, this opens up a potentially dangerous hole because users can now enter JS code to be rendered on the front-end. A malicious user can add booby-trapped code so that when you navigate to the site, that code executes on your computer.

[![](https://web.archive.org/web/20240420003312im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-beaver-builder-customizer-code-tab-01.png)](https://web.archive.org/web/20240420003312/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-beaver-builder-customizer-code-tab-01.png)

Any plugin where you allow the user access needs to be reviewed for this type of dangerous input.

With Beaver Builder you can remove these inputs (yet another reason why we prefer it for SaaS projects over something like Elementor).

To remove the CODE tab from the customizer, you need to add the following code to your template site custom plugin:

function remove\_fl\_code( $wp\_customize ) {
    $wp\_customize->remove\_panel( 'fl-code' );
}
add\_action( 'customize\_register', 'remove\_fl\_code', 11 );

If you’re using a class, the **add\_action** function call will change slightly to include the use of array() when referencing the hooked function.

Each Beaver Builder module also includes an option to set JS code so you’ll need to remove that as well:

add\_filter("fl\_builder\_main\_menu", function ($views) {
      unset($views\['main'\]\['items'\]\[50\] ); //Layout CSS & Javascript
      unset($views\['main'\]\['items'\]\[60\] ); //Global Settings
      return  $views;
});

If you’re using a class, the **add\_filter** function call will change slightly to include the use of array() when referencing the hooked function.

[![](https://web.archive.org/web/20240420003312im_/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-beaver-builder-customizer-code-tab-03.png)](https://web.archive.org/web/20240420003312/https://wpclouddeploy.com/wp-content/uploads/2024/02/wpcd-beaver-builder-customizer-code-tab-03.png)

### More Topics In WordPress SaaS

*   [WordPress SaaS Introduction](https://web.archive.org/web/20240420003312/https://wpclouddeploy.com/documentation/wpsaas/wordpress-saas-introduction/)
*   [CNAMES & Your WordPress SaaS](https://web.archive.org/web/20240420003312/https://wpclouddeploy.com/documentation/wpsaas/cnames-your-wordpress-saas/)
