#Webpack

Webpack has become one of the most important tools for modern web development. 

* a module bundler for your JavaScript
* transform other front-end assets
  * HTML and CSS, images, etc.
  * use other flavors of those assets (Jade, Sass & ES6, etc)
* control the number of HTTP requests your app is making
* easily consume packages from npm

##4 Core Concepts

* Entry point(s)
  * Where should webpack start looking for dependencies?
* Output
  * Where should it store the bundle(s)?
* Module loaders
  * Transform the code
* Plugins

  
  https://youtu.be/8DDVr6wjJzQ?t=4m26s  Add a notated image of the webpack config.  arrows and notes about the node path module, __dirname, 

addiing `babel` to `webpack.config.js` like this `webpack.config.babel.js` will allow you to use es2016 code in your config file

###Loaders & Plugins

###Specifying an entry point

###Webpack dev server

###minifying & source maps

###development vs production

###Tree Shaking
Tree shaking excludes exports from modules where it can be detected the export is not used.  Uglify the deletes the dead code. ~ Kent C Dodds

###More Info

[A Beginner’s Guide to Webpack 2 and Module Bundling - Sitepoint ](https://www.sitepoint.com/beginners-guide-to-webpack-2-and-module-bundling/)ja