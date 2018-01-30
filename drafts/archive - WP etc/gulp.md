#Gulp

* simulate the server environment where you host your code.
* move files around your project directory
* place them in a development directory where you run a web server
* compile, minify and concatenate files( validate?)
* get your code's footprint down to the minimum making it ready for shipping to production.


##3 Main Gulp Commands
1. gulp.task()
2. gulp.src()
3. gulp.dest()
  * The Node.js pipe() method to copy files from one folder to another.


##three main folders

* src folder = source files, pre-processed, un-minified
* tmp = development files, pre-processed, un-minified. You run the web server here.
* dist = production files, processed, minified

##Workflow

* Create separate tasks for pipeing HTML, CSS and JavaScript files from src to tmp.
* Combine the HTML, CSS and JavaScript tasks into one main ‘copy’ task to copy all the files with one command
* "injecting dependencies" - reference all files automatically in your main index.html using an ‘inject’ task
* run a dev server on the tmp folder
* ‘watch’ for changes while the server is running
  * enable live reloading on the local dev server
  * Finally ‘build’ the production files in the dist directory

Delete tmp and dist before pushing to GitHub. (Or just add them to your .gitignore)




-----
resources:
[https://hackernoon.com/how-to-automate-all-the-things-with-gulp]()

[https://www.sitepoint.com/introduction-gulp-js]()