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

## run webpack with debug mode
```js
webpack
```


** the result after running webpack**
```text
Hash: 15ffb14176c2041e66df
Version: webpack 3.11.0
Time: 988ms
         Asset     Size  Chunks                    Chunk Names
scripts.min.js  2.19 MB       0  [emitted]  [big]  main
   [0] ./js/scripts.js 50 bytes {0} [built]
   [1] ./js/module1.js 53 bytes {0} [built]
   [3] ./js/module2.js 3.31 kB {0} [built]
   [5] (webpack)/buildin/global.js 509 bytes {0} [built]
   [6] (webpack)/buildin/module.js 517 bytes {0} [built]
    + 2 hidden modules
```



## Check the version
```js
webpack -v
//3.11.0
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



## References:
- [Webpack Tutorial - Replace Gulp/Grunt plugins with a single tool](https://www.youtube.com/watch?v=9kJVYpOqcVU)
- [Webpack official site](https://webpack.js.org/guides/installation/#src/components/Sidebar/Sidebar.jsx)
- [webpack.config.js sample](https://gist.github.com/learncodeacademy/25092d8f1daf5e4a6fd3)
