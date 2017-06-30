# Modern Front End Developer Workflow - Gulp & Node
<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/npm.png" width="150px" height="auto" />
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/node.png" width="80px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/browsersync.png" width="100px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/babel.png" width="100px" height="auto"/>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/gulp.jpg" width="80px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/postcss.png" width="100px" height="auto"/>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/webpack.png" width="100px" height="auto">
</p>

## Index

[Fundamental Concepts](#fundamentals)

[Pre-requisites](#prerequisites)

[Initializing a new project](#initializing-a-new-project)


## Fundamental Concepts

### What is Node/Node.js?
Node.js is an open source server framework that allows you to run JavaScript on the server.
Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. It uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

### What is npm?
Node Package Manager. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.A repository of Node code, as well as third-party libraries such as Bootstrap and jQuery. Allows for easy installation and updating from the command line.

### What is Gulp?
Gulp is a toolkit for automating painful or time-consuming tasks in your development workflow, so you can stop messing around and build something.

## Pre-requisites

### Install Node.js
Go to [https://nodejs.org/en/](https://nodejs.org/en/), Download the installer and set it up on your system. Restart Computer.

### Install npm
Voila! npm comes with Nodejs. No need to install it.

### Check that you have node and npm installed
To check if you have Node.js installed, run this command in your terminal:
   ` node -v`
    
To confirm that you have npm installed you can run this command in your terminal:
   ` npm -v`
    
## Initializing a new project

**1.** Bash into the project folder & run `npm init`. This sets up NPM for the project, and creates *package.json*, which will store config info on the packages used in the project.It will ask some questions before creating the package.json file.

**2.** Run `npm install jquery --save`. (If jquery is needed in the project)
(If node modules get deleted or outdated, run `npm install` to get fresh version of packages listed in package.json)

**3.** Install gulp cli. `npm install gulp-cli -global`. Run `gulp -v` to check CLI version.

**4.** Install gulp package in your project. `npm install gulp --save-dev`

**5.** Create *gulpfile.js* in project root `touch gulpfile.js `. Add placeholder tasks to the file:

```
var gulp = require(‘gulp’);

	gulp.task('default', function() {
  		console.log("Yay, Gulp default task");
	});

	gulp.task(‘html’, function() {
		console.log(“Woohoo!! html task”);
	});

	gulp.task(‘styles’, function() {
		console.log(“Yippee..styles task”);
	});
```

**6.** Install the gulp-watch package `npm install gulp-watch --save-dev`

add to *gulpfile.js*:
```
watch = require('gulp-watch’);

gulp.task('watch', function() {
  watch('./app/index.html',
    function(){
      gulp.start('html');
    });
});
```

**7.** Set up **post-css** with **autoprefixer** (automatic webkit prefixes to ensure browser css compatibility); **simple-vars** (use variables in css); **nested** (nesting selectors in css) and **import** (write modular css across different files).

```
npm install gulp-postcss --save-dev
npm install autoprefixer --save-dev
npm install postcss-simple-vars --save-dev
npm install postcss-nested --save-dev
npm install postcss-import --save-dev
```

add to *gulpfile.js*:
```
postcss = require('gulp-postcss’),
autoprefixer = require(‘autoprefixer’),
cssvars = require('postcss-simple-vars’),
nested = require('postcss-nested’),
cssImport = require('postcss-import');


gulp.task('styles', function() {
  return gulp.src('app/assets/styles/styles.css')
    .pipe(postcss([cssImport, cssvars, nested, autoprefixer]))
    .pipe(gulp.dest('app/temp/styles'));
});
```
