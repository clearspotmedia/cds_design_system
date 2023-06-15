# Design System module for LocalGov sites
Module for a Design System in LocalGov Drupal

This module is designed to be used in partnership with the Design System Theme.

**Read aout the Design System Theme before using this module!**
[https://github.com/clearspotmedia/cds_design_system](https://github.com/clearspotmedia/localgov_design_system/)

## Features

### Content type
This module provides a content type called **Design and content guidelines**.  
This content type offers a more structured editing experience for design system authors and an improved front end interface for Design System pages including responsive navigation.

Design system pages now contain a headline, summary and body area, as well as a new 'Page section' paragraph type that enables editors to organise longer page content into headed sections.

### Primary and secondary navigation

To structure content you will create and assign 'parent' and 'child' pages. 'Parents' act as sections while 'children' are pages within sections.
These sections and child pages are output into well considered responsive menus for navigation.

The front end interface closely replicates the GDS design system navigation structure. https://design-system.service.gov.uk/

### Auto contents menu

Page sections added by editors (see content type above) are rendered as h2 titles and text in the content area. Each title is also automatically presented as an anchor link within the page sidebar 'secondary navigation' under the current highlighted page.

### Platform taxonomy

Add your own taxonomy and choose which to show on design system pages, for example to indicate platform support for components or styles.

### Summary of features with both theme and module installed:

* designed to be installed as a LocalGov microsite or a standard LocalGov Drupal site installation (Standard installation to be tested)
* search the design system with LocalGov search
* new paragraph type for adding headed sections and content in design system pages
* automatic contents menu based on page section headings
* taxonomy to show platform support for components
* responsive primary and secondary navigations
* simple white labelled sub theme that uses LocalGov Base as its base theme



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

#### Design system menu
This menu is not automatically available in every microsite.  It has to be manually **added** from a microsite dashboard's *Menus* tab.

## Notes
- **Restrict** the `Raw HTML` text format to trusted Drupal user roles only.  This text format can be used to introduce malicious content such as Cross-site scripting markup.

## Theming
### localgov_page_header_block template variables
- parent_root_label: Label of the root page in the active menu trail.
