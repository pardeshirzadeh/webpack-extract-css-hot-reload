### webpack-extract-css-hot-reload

This simple loader was created to hot reload css files which have been extracted with `extract-text-webpack-plugin`. Based on [css-hot-loader](https://github.com/shepherdwind/css-hot-loader/).

### Install

First install the package from npm

```sh
$ npm install webpack-extract-css-hot-reload --save-dev
```
### Usage

Update your `webpack.config.js`. For example

```typescript
module: {
  rules: [
    {
      test: /\.css$/,
      loader: ['webpack-extract-css-hot-reload'].concat(ExtractTextPlugin.extract([
        {
          loader: 'css-loader',
        }, {
          loader: 'postcss-loader',
        },
      ] as string[]),
    },
  ]
}
```
NOTE: `webpack-extract-css-hot-reload` should be defined before `extract-text-webpack-plugin`.

Tag the stylesheets which need hot reloading with `data-hot`.

index.html
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
    <title>Example title</title>

    <!-- Roboto font -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">

    <!-- Own styling -->
    <!-- This stylesheet needs to hot reload -->
    <link rel="stylesheet" href="build/styles.css" data-hot>
  </head>

  <body>
    <div id="root" />

    <script type="text/javascript" src="build/bundle.js"></script>
  </body>
</html>
```

That's all! You're good to go. :)

### Options
#### selector
If you don't like `data-hot` for tagging hot reloadable content, then you can pass a custom HTML attribute. For example `'webpack-extract-css-hot-reload?selector=data-lukewarm'`.

### License

MIT License
