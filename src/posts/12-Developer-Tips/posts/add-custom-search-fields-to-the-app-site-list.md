---
title: "Add Custom Search Fields To The App (Site) List"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Add Custom Search Fields To The App (Site) List
  parent: 12-Developer-Tips
  order: 6
---

Did you add some custom fields to the DevelopVIDeploy APP custom post type (‘wpcd\_app’), but now want the search in the app list to include those fields? Or maybe you want to include one of our APP CPT fields that we aren’t searching now (eg: the _wpcd\_site\_status\_push_ field.)

Here’s how you would do that.

Assuming you already have a custom plugin on your DVI site, you need to add the following to let WordPress know you want to hook into one of our hooks:

add\_filter( 'wpcd\_app\_search\_fields', array( $this, 'wpcd\_app\_my\_custom\_search\_fields' ), 10, 1 );

That line goes into the CONSTRUCTOR function of your class. Or, if you’re not using a PHP class, use this instead.

add\_filter( 'wpcd\_app\_search\_fields',  'wpcd\_app\_my\_custom\_search\_fields' ) );

Then, add this function:

/\*\*
  \* Include additional search fields when searching the app list.
  \*
  \* Filter Hook: wpcd\_app\_search\_fields
  \*
  \* @see class-wpcd-posts-app.php - function wpcd\_app\_extend\_admin\_search
  \*
  \* @param array $search\_fields The current list of fields.
  \*/
public function wpcd\_app\_my\_custom\_search\_fields( $search\_fields ) {
    /\* Replace your fields in the array below  \*/
    $our\_search\_fields = array(
        '_wpcd\_site\_status\_push_',
        '_your\_second\_custom\_field_',
        '_your\_third\_custom\_field_',
    );
    $search\_fields = array\_merge( $search\_fields, $our\_search\_fields );
    return $search\_fields;
}

You just need to replace your field names in the array.

If you’re not using a PHP class, you’ll need to remove the ‘public’ from the function definition.

Now, when you search for a value using the search box in the app/site list, it should pick up any values in your custom fields and filter the list accordingly.

- - -

### More Topics In Developer Tips

*   [Using Visual Studio Code With DevelopVIDeploy](https://web.archive.org/web/20240420015230/https://wpclouddeploy.com/documentation/developer-tips/using-visual-studio-code-with-wpclouddeploy/)
*   [How To Remove The DEPLOY A NEW WORDPRESS SERVER Button](https://web.archive.org/web/20240420015230/https://wpclouddeploy.com/documentation/developer-tips/how-to-remove-the-deploy-a-new-wordpress-server-button/)
*   [How To Make Edits Directly In Core Files And Not Lose Changes On Upgrades](https://web.archive.org/web/20240420015230/https://wpclouddeploy.com/documentation/command-line-scripts/advanced-backups/how-to-make-edits-directly-in-core-files-and-not-lose-changes-on-upgrades/)
