# Introduction

<p class="uk-text-lead">Get familiar with the basic setup and overview of UIkitty.</p>

UIkitty is UIkit for Drupal 8. To use UIkitty, you must either download and install Drupal 8 and then download and install UIkitty. For other packages and links to a CDN, head to the [installation guide](installation.md) to learn more.

<a class="uk-button uk-button-primary" href="https://uikitty.com/3.x/download">Download UIkitty 3.x</a>

***

## Package contents

The Zip file contains the prestructured Drupal Theme files and working distribution of UIkit, which is everything you need to get started. Later, you might want to [install and compile UIkit](installation.md) yourself and also [create your own UIkitty theme](less.md).

| Folder    | Description |
| --------- | --- |
| `/css`    | Contains the UIkitty CSS and a right-to-left version. |
| `/js`     | Contains the UIkitty JavaScript and the Icon Library JavaScript. |

***

## HTML markup

Add the compiled and minified CSS and JavaScript to the header of your HTML5 document. [jQuery](http://jquery.com/download/) is required as well. Also include the UIkitty icon library. For your basic setup, that's it.

```html
<!DOCTYPE html>
<html>
    <head>
        <title></title>
        <link rel="stylesheet" href="css/uikit.min.css" />
        <script src="js/jquery.js"></script>
        <script src="js/uikit.min.js"></script>
        <script src="js/uikit-icons.min.js"></script>
    </head>
    <body>
    </body>
</html>
```

Once you have included UIkitty into your document, take a look at the available components and create your own markup inside the `<body>` element of your page.

***

## UIkitty autocomplete for your editor

Using UIkitty works best if you have a solid code editor, for example [Sublime Text](https://www.sublimetext.com/) or [Atom](https://atom.io/). To be even more efficient, we recommend that you install one of the autocomplete plugins for your favorite IDE or code editor. This saves a lot of time, as you won't have to look up and type all UIkitty classes and markup.

- [Autocomplete plugin for Sublime Text 3](https://github.com/uikit/uikit-sublime)
- [Autocomplete plugin for Atom](https://atom.io/packages/uikit-atom)

***

## Browser support

The following table lists the versions that UIkitty is tested on. "Latest" means that it works just fine on all recent versions of that browser. With many browser moving towards a rolling release strategy, pinning down browser support to a specific version has become a little tricky in recent years. Long story short: UIkitty will work on pretty much any modern browser.

| ![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) |
| --- | --- |
| Latest | Latest | Latest | 10+ | 7.1+ | Latest |
