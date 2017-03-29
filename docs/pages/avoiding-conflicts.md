# Avoiding conflicts

<p class="uk-text-lead">Use a custom prefix and the scope mode to make UIkitty work in any environment.</p>

By default, all classes and attributes in UIkitty start with the `uk-` prefix. This avoids name collisions when introducing UIkitty to existing projects or when combining it with other frameworks. UIkitty allows to change that prefix. This even allows to use multiple versions of UIkitty alongside each other. In addition, the scope mode allows to limit the UIkitty styles to only affect certain parts on your pages.

***

## Custom prefix

Using a custom prefix allows using multiple versions of UIkitty on the same page. This might be needed when you are building something like a CMS plugin. In such cases, you do not know what other versions of UIkitty might be loaded, so it is a good idea to use a custom prefix.

When you have [setup UIkitty from Github source](installation.md#compile-from-github-source), you can compile it with a custom prefix. If you choose a custom prefix, for example `xyz`, all attributes and classes will now start with that prefix, for example `xyz-grid` instead of `uk-grid`. The global JavaScript object `UIkit` will also be renamed to `xyzUIkit`.


```sh
npm run prefix -- -p xyz # replace xyz with your custom prefix.
```

The script will go through all CSS files in the `/dist` folder and replace them with your custom prefix version.

**Note** The Base component will still include styles that affect some base HTML elements. To avoid this, either create a [custom build](less.md) without including the Base component, or use the scoped mode.

***

## Scope mode

Using a scoped version of UIkitty allows you to limit styles to only apply to a certain part of your document. This might be needed in environments of admin interfaces, such as the backend of WordPress or Joomla. When you have [setup UIkitty from Github source](installation.md#compile-from-github-source), you can recompile UIkitty as a scoped version.

```sh
npm run scope
```

You will find the generated CSS and JS files in the `/dist` folder. To use the scoped version, wrap the document section with your UIkitty markup in an element with the `.uk-scope` class.

```html
<!DOCTYPE html>
<html>
    <head>
        ...
    </head>
    <body>

        <!-- non UIkitty markup -->
        ...

        <div class="uk-scope">
            <!-- your UIkitty markup -->
            ...
        </div>
    </body>
</html>
```
