# Webpack

## Installation
```js
npm init                // create package.json
npm install -S webpack  // install webpack with dependencies
npm install -g webpack  // install webpack globally
```

## webpack.config.js
```js
var debug = process.env.NODE_ENV !== "production";
var webpack = require('webpack');

module.exports = {
  context: __dirname,
  devtool: debug ? "inline-sourcemap" : null,
  entry: "./js/scripts.js",
  output: {
    path: __dirname + "/js",
    filename: "scripts.min.js"
  },
  plugins: debug ? [] : [
    new webpack.optimize.DedupePlugin(),
    new webpack.optimize.OccurenceOrderPlugin(),
    new webpack.optimize.UglifyJsPlugin({ mangle: false, sourcemap: false }),
  ],
};
```

## run webpack and compile js files
```js
webpack
```

**Compiled `scripts.js` to `script.min.js`**
```js
require('./module1.js');
require('./module2.js');
```



**HTML**
```html
<!DOCTYPE html>
<html>
<head>
	<title>Some Page</title>
</head>
<body>
<h1>My Webpack Page</h1>
<script src="js/scripts.min.js"></script>
</body>
</html>
```

## npm installation flag
![npm-install-option](http://www.hirokoymj.com/images/Git/npm-install-flag.png)

## References:
- [Webpack Tutorial - Replace Gulp/Grunt plugins with a single tool](https://www.youtube.com/watch?v=9kJVYpOqcVU)
- [Webpack official site](https://webpack.js.org/guides/installation/#src/components/Sidebar/Sidebar.jsx)
- [webpack.config.js sample](https://gist.github.com/learncodeacademy/25092d8f1daf5e4a6fd3)
