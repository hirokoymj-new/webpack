# Webpack

## Installation
**Installed webpack**

```js
npm init                // create package.json
npm install -S webpack  // install webpack with dependencies
npm install -g webpack  // install webpack globally
```

**Installed jQuery and lodash for this demo**
```js
npm install jQuery
npm install lodash
```


## Create webpack.config.js
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

## Check package.json
jquery and lodash is also installed for this demo. 

```js
{
  "name": "module-loaders",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "jquery": "^3.3.1",
    "lodash": "^4.17.5",
    "webpack": "^3.11.0"
  }
}
```


## run webpack to compile js files
**Run with debug mode**

```js
webpack
```


**Run with production mode**
```js
NODE_ENV=production webpack
```


**Compiled following files to `script.min.js`**
- js/module1.js
- js/module2.js
- js/scripts.js


```js
//scripts.js
require('./module1.js');
require('./module2.js');
```


**Run a html file**

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
