# Design system

## Features
This module provides a content type called **Design and content guidelines**.  The body field of this content type defaults to the `Raw HTML` text format.  This makes it easy to enter pure HTML markup.  Such markup is helpful while documenting the Design system (AKA Style guide) of a site.  Also provided:
- A separate menu.
- Two menu blocks.  These should be placed in the **breadcrumb** and **first sidebar** regions so that the menu appears before the page content.
- URL alias pattern.

## Installation steps
1. Download this module and place it inside the `modules/custom/` directory of your site.
2. *Unless* using the localgov_design_system theme, edit the `config/optional/block.block.design_system_menu_primary.yml` and `config/optional/block.block.design_system_menu_secondary.yml` files of this module and replace `localgov_design_system` with the machine id of the Drupal theme in use.  For example, if you are using the Bartik theme, replace `localgov_design_system` with `bartik`.  Depending on the theme regions available, you may have to update the `region` value as well.
3. Now try the following commands:

  ```
  $ composer require prismjs/prism
  $ mkdir -p web/libraries/prism; cp vendor/prismjs/prism/prism.js web/libraries/prism/; cp vendor/prismjs/prism/themes/prism-okaidia.css web/libraries/prism/prism.css # Ensures prism.js and prism.css are present in libraries/prism/ inside the docroot.
  $ composer require drupal/prism drupal/block_class
  $ drush --yes pm:enable cds_design_system
  ```

## Usage
- Create *Design and content guideline* pages like any other page.  The default text format for the body field is `Raw HTML` which allows you to enter any HTML markup.  Other text formats may be available and those can be used as well *if necessary*.
- By default, new pages are not placed in the Design system menu.  To do so, look for the `Menu settings` accordion within the node edit page's sidebar.  Once found, expand the accordion and tick the `Provide a menu link` checkbox.

### LocalGov Microsites compatibility
This module is ready for use within LocalGov Microsites.  

## Notes
- **Restrict** the `Raw HTML` text format to trusted Drupal user roles only.  This text format can be used to introduce malicious content such as Cross-site scripting markup.
