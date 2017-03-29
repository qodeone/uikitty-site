# Less

<p class="uk-text-lead">Learn how to modify the UIkitty styling and create your own theme.</p>

When you have [installed UIkit](installation.md) with Less sources, you can compile it and add your own custom theme. [Less](http://lesscss.org/) is the language that the UIkitty styles are written in. This allows you to include customizations in the build process, rather than manually overwriting a lot of CSS rules by hand.

***

## Use your own build process

To include UIkitty in your project's build workflow, you need to import the core UIkitty styles (`uikit.less`) or UIkitty with its default theme (`uikit.theme.less`) into your project's own Less file. This main Less file then needs to be compiled in any way you like. Read the [official Less docs](http://lesscss.org/usage/) if you are unsure how to compile Less.

```less
// Import UIkitty default theme (or uikit.less with only core styles)
@import "bower_components/uikit/src/less/uikit.theme.less";

// Your custom code goes here, e.g. mixins, variables.
// See "how to create a theme" below for more info.
```

***

## Use included build process

If you are want to change the styling of UIkit, you can use its build process to create a differently themed version of the CSS, that you can then include in your project. That way you do not need to set up your own build process.

To include your own Less theme in the build process, create a `/custom` directory, which will contain all of your custom themes.

**Note** The `/custom` folder is listed in `.gitignore`, which prevents your custom files from being pushed into the UIkitty repository. You might also have the `/custom` directory as your own Git repository. That way your theme files are under version control without interfering with the UIkitty files.

Create a file `/custom/my-theme.less` (or any other name) and import the core UIkitty styles (`uikit.less`) or UIkitty with its default theme (`uikit.theme.less`).

```less
// Import UIkitty default theme (or uikit.less with only core styles)
@import "../src/less/uikit.theme.less";

// Your custom code goes here, e.g. mixins, variables.
// See "how to create a theme" below for more info.
```

To compile UIkitty and your custom theme into CSS, run the npm task `compile` .

```sh
# Run once to install all dependencies
npm install

# Compile all source files including your theme
npm run compile

# Watch files and compile automatically everytime a file changes
npm run watch
```

The generated CSS files will be located in the `/dist/css` folder.

**Note** The custom theme is also available in the test files, just navigate your browser to the index of the `/test` directory and select your theme from the Dropdown menu.

***

## Create a UIkitty theme

When you have setup a file to put in your own Less code, you can get started to theme UIkitty the way you want. If you have never used Less before, check out the [language features](http://lesscss.org/features/). When working with the UIkitty Less sources, we have a few recommendations.

### Use variables

A lot of customization is possible by simply overwriting the values of already declared variables. You can find all variables for each component inside their Less files of the framework and override them in your theme.

First, find a Less variable you want to change inside the UIkitty source. For example, the global link color is defined in `/src/less/components/variables.less`:

```less
// default value
@global-link-color: #4091D2;
```

Then, overwrite the default by setting a custom value inside your own file, i.e. in `/custom/my-theme.less`:

```less
// new value
@global-link-color: #DA7D02;
```

The compiled CSS will then have your custom value. But not only has the global link color changed. Many components make use of the `@global-*` variables to infer their own colors, and just adapt them slightly. That way you can rapidly create a theme by just changing some global variables.

### Use hooks

To prevent overhead selectors, we use Mixins from [Less](http://lesscss.org), which hook into predefined selectors from the UIkitty source and apply additional properties. Selectors don't have to be repeated throughout all documents and global changes can be made much more easily.

First, find a rule that you want to extend by looking through the component's Less file, for example `/src/less/components/card.less` for the Card component:

```less
// CSS rule
.uk-card {
    position: relative;
    box-sizing: border-box;

    // mixin to allow adding new declarations
    .hook-card;
}
```

Then, inject additional CSS by using the hook inside your own Less file, i.e. in `/custom/my-theme.less`:

```less
// mixin to add new declaration
.hook-card() { color: #000; }
```

### Miscellaneous hooks

Should there be neither a variable nor a hook available, you can also create your own selector. To do so, use the _.hook-card-misc_ hook and write your selector inside. This will sort your new selector to the right place of the compiled CSS file. Just add the following lines to your own Less file, i.e. to `/custom/my-theme.less`:

```less
// misc mixin
.hook-card-misc() {

    // new rule
    .uk-card a { color: #f00; }
}
```

## How to structure your theme

In the examples above, we have added all custom rules directly to `/custom/my-theme.less`. When you change a few variables but are happy with the rest, this is perfectly fine. However, for larger customizations, we recommend to only use this file as an entry point for the Less compiler. You should better sort all rules into single files per component inside of a subfolder. This is the same structure that you can find in the default theme `/src/less/uikit.theme.less`.

**Note** The example assumes you are building a theme in the `/custom` directory of the full UIkitty project. You can adapt these paths if you have set up your own build process.

```html
custom/

    <!-- entry file for Less compiler -->
    my-theme.less

    <!-- folder with single Less files -->
    my-theme/

        <!-- imports all components in this folder -->
        _import.less

        <!-- one file per customized component -->
        accordion.less
        alert.less
        ...
```

The entry point for the Less compiler, `/custom/my-theme.less`:

```less
// Core
@import "../../src/less/uikit.less";

// Theme
@import "my-theme/_import.less";
```

Your theme folder has one file which imports all single component customizations, `custom/my-theme/_import.less`:

```
@import "accordion.less";
@import "alert.less";
// ...
```
