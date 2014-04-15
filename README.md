brackets-sass
===========================

Compiles *.sass and *.scss files when changed.

## Preferences

These options are passed through to [node-sass](https://github.com/andrew/node-sass).

Reference: [Sample project](https://github.com/jasonsanjose/brackets-source-map-demo-files) and `.brackets.json` preferences file.

### sass.output
`output` is a `String` relative file path for the output CSS file.
Default: `<filename>.css`.

### sass.options
Derived from [node-sass](https://github.com/andrew/node-sass) README.

#### includePaths
`includePaths` is an `Array` of path `String`s to look for any `@import`ed files. It is recommended that you use this option if you are using the `data` option and have **any** `@import` directives, as otherwise [libsass] may not find your depended-on files.
Default: `[<empty>]`

#### imagePath
`imagePath` is a `String` that represents the public image path. When using the `image-url()` function in a stylesheet, this path will be prepended to the path you supply. eg. Given an `imagePath` of `/path/to/images`, `background-image: image-url('image.png')` will compile to `background-image: url("/path/to/images/image.png")`
Default: `null`

#### outputStyle
`outputStyle` is a `String` to determine how the final CSS should be rendered. Its value should be one of `'nested'` or `'compressed'`.
[`'expanded'` and `'compact'` are not currently supported by [libsass]]
Default: `nested`

#### sourceComments
`sourceComments` is a `String` to determine what debug information is included in the output file. Its value should be one of `'none', 'normal', 'map'`. The default is `'none'`.
The `map` option will create the source map file in your CSS destination.
[Important: `souceComments` is only supported when using the `file` option, and does nothing when using `data` flag.]
Default: `map`

#### sourceMap
If your `sourceComments` option is set to `map`, `sourceMap` allows setting a new path context for the referenced Sass files.
The source map describes a path from your CSS file location, into the the folder where the Sass files are located. In most occasions this will work out-of-the-box but, in some cases, you may need to set a different output.
Default: `<filename>.css.map`.

### Sample .brackets.json File

```
{
    "path": {
        /* default options */
        "sass/bootstrap.scss": {
            "sass.enabled": true,
            "sass.options": {
                "output": "bootstrap.css",
                "includePaths": [],
                "imagePath": null,
                "sourceComments": "map",
                "sourceMap": "bootstrap.css.min"
                "outputStyle": "nested"
            }
        },
        /* disable compiling @import files in this project */
        "sass/bootstrap/*.scss": {
            "sass.enabled": false
        }
    }
}
```

## Future Plans

* Live Preview support