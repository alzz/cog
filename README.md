## Nimbus: Acquia D8 Starter Theme

Nimbus is a developer-focused base theme and starterkit intended as a minimalist starting point for custom theming. Nimbus provides the least amount of code to get started, but still packed with utilities and documentation to start quickly.

### Features

* Responsive containers built on Susy grid system
* Initial SMACSS file architecture
* Core *.yml and theme dependencies
* Modular gulp tasks for compiling and linting
* Living style guide construction via KSS-node

## Set up your Theme with Nimbus

### Create your Starter Theme

1. In your `themes/` directory create the `contrib` and `custom` directories
2. Download Nimbus into the `themes/contrib` folder and enable Nimbus using `drush en nimbus`
3. Set Nimbus as your default theme: `drush config-set system.theme default nimbus`
4. To create a subtheme using the default options use `drush nimbus "MyTheme"`
5. Enable your new `MyTheme` theme with `drush en mytheme` which is located in `themes/custom`
6. Set `MyTheme` as your default theme `drush config-set system.theme default mytheme`

Available options for creating your new theme `drush help nimbus`

### Setup locally for development

Once you have created a custom subtheme, you will know follow these quick steps to start. If you would like to review extension explanations of these steps, be sure to read the XXXXXXX

1. Navigate to `themes/custom/mytheme` folder in your terminal
2. Install Node.js with `./install-node.sh 4.4.4` and then point to the proper version with `source ~/.bashrc && nvm use --delete-prefix 4.4.4` 
3. If you are not using avn then run `nvm use 4.4.4` when closing and reopening your session
4. If you choose to use avn follow the instructions here XXXXX
5. Install local library dependencies `npm run install-tools`
6. To confirm Gulp and other items are instantiated `npm run build`


## Theme Architecture Overview

### Files & Folder Structure

The core files are fairly minimal when setting up a new theme. These files are considered as the initial configurable pieces. 

```
|-- css/  (generated css) 
|-- gulp-tasks/ (modular gulp task files)
|-- images/  (theme images)
|-- js/  (compiled js)
|-- sass/  (SMACSS based sass setup)
|-- gulpfile.js  (configured gulp file) 
|-- install-node.sh (bash script to install nvm and node)
|-- logo.png (placeholder logo png file)
|-- logo.svg (placeholder logo svg file)
|-- node_modules/  (modules generated by npm)
|-- package.json  (configured to load dependencies by npm)
|-- README-SETUP.md (Quickstart documentation theme)
|-- screenshot.png (placeholder theme screenshot file)
|-- [theme-name].info.yml (theme config file)
|-- [theme-name].libraries.yml (starter libraries file to load theme assets)
|-- [theme-name].theme (file to use for preprocess functions)
|-- theme-settings.php (file to use for making theme settings available in the GUI)

```


### Sass Structure

Setup of the Sass files so that they are properly broken out in partials and according to the [SMACSS](https://smacss.com/) methodologies.

```
sass/
  |-- _config.scss
  |-- _reset.scss
  |-- base/
  |-- layout/
  |-- components/
  |-- state/
  |-- style-guide-only/
  |---- homepage.md
  |---- kss-only.scss
  |-- style.scss
```

* **_config.scss** this configuration is housing common mixins, variables, or similar, normally you would want to break these out in separate partials
* **styles.scss**  the manifest file that imports all the partials or folders with globbing 
* **base/** intended as the baseline pstyles that you extend upon and will include things like resets, global typography, or common form selectors.
* **layout/**  for structural layout that can apply to both the outer containers like the sidebars or headers, but also on inner structual pieces.
* **components/** these module files are the reusable or component parts of our design.
* **state/** modules will adjust when in a particular state, in regards to targeting how changes happen on contextual alterations for regions or similar  
* **style-guide-only/** contains homepage.md which provides the content for the Overview section of the styleguide, and kss-only.scss which generates a css file for styling needed by a component for display in the style guide, but not loaded into the actual theme  


### JavaScript Files

An example JS file `theme.js` is added by default in the `js/` folder. This file contains sample code wrapped in the `Drupal.behaviors` code standard. This JS file is added to the theme with the following portion of the code from `[theme-name].libraries.yml`

```
lib:
  js:
    js/theme.js: {}
```

### Grid & Region Structure

The Nimbus grid structure was setup with the intent of having a very minimalist starting point in terms to be confined within. 

TODO: grid references
TODO: file examples
TODO: visual region image 


## Documentation & Code Examples


* [Front end best-practices](_theming-guide/front-end.md)
* [Code reference for this theme](_theming-guide/preprocessing.md)
* [SMACSS methodologies](https://smacss.com/) 
* [Drupal.org Guide for Theming Drupal 8](https://www.drupal.org/theme-guide/8) 
* [Documentation for your THEMENAME.info.yml](https://www.drupal.org/node/2349827)
* [Documentation for your THEMENAME.libraries.yml](https://www.drupal.org/theme-guide/8/assets)

## Build Notes

At the current time warnings are displayed for graceful-fs and lodash, these are known issues with gulp 3.x and will no longer be an issue once gulp 4.x is available.

[graceful-fs warning](https://github.com/gulpjs/gulp/issues/1571)
[lodash warning](https://github.com/gulpjs/gulp/issues/1485)

## License, support, and contribution

Nimbus is provided as an open source tool in the hope that it will enabled
developers to easily generate new Drupal projects that conform to Acquia 
Professional Services' best practices.

Please feel free to contribute to the project or file issues via the GitHub 
issue queue. When doing so, please keep the following points in mind:
 
* Nimbus is distributed under the GPLv3 license; WITHOUT ANY WARRANTY.
* The project maintainers make no commitment to respond to support requests, 
  feature requests, or pull requests.
* All contributions to Nimbus will be reviewed for compliance with Drupal Coding
  Standards and best practices as defined by the project maintainer.

Nimbus work is currently being tracked in the [nimbus GitHub issue queue]
(https://github.com/acquia-pso/nimbus/issues) and organized via a
[Waffle.io Kanban Board](https://waffle.io/acquia-pso/nimbus).

When making a pull request related to an issue, use the keywords 'Connects to #123' in your commit message to automatically relate the PR to the issue on the kanban board.
