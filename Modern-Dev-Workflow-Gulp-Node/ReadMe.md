# Modern Front End Developer Workflow - Gulp & Node
<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/npm.png" width="300px" height="auto" />
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/node.png" width="150px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/browsersync.png" width="300px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/babel.png" width="300px" height="auto"/>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/gulp.jpg" width="120px" height="auto">
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/postcss.png" width="300px" height="auto"/>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/webpack.png" width="300px" height="auto">
</p>

## Index

[Fundamental Concepts](#fundamentals)

[Pre-requisites](#prerequisites)

[Initializing a new project](#initializing-a-new-project)

[BrowserSync](#browserSync)

[PostCSS Mixins](#postcss)

[Responsive Images](#responsive-images)


## Fundamental Concepts

### What is Node/Node.js?  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/node.png" width="60px" height="auto" />
Node.js is an open source server framework that allows you to run JavaScript on the server.
Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. It uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

### What is npm? <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/npm.png" width="70px" height="auto">
Node Package Manager. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.A repository of Node code, as well as third-party libraries such as Bootstrap and jQuery. Allows for easy installation and updating from the command line.

### What is Gulp? <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/gulp.jpg" width="50px" height="auto">
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

**7.** <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/postcss.png" width="100px" height="auto"/>Set up **post-css** with **autoprefixer** (automatic webkit prefixes to ensure browser css compatibility); **simple-vars** (use variables in css); **nested** (nesting selectors in css) and **import** (write modular css across different files).
  
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
**8.** Adding stylesheet to *app/index.html*:

```
<link rel="stylesheet" href="temp/styles/styles.css">
```

**8.** CSS Architecture - Modular CSS
````
|-app
	index.html
		|- assets
			|-fonts
			|-images
			|-styles
				styles.css
				|-base
					_global.css
				|-modules
					_header.css
					_footer.css

````

**9.** Import css modules in *styles.css* 

```
@import “base/_global.css”;
@import “modules/_footer.css”;

```

## BrowserSync
Update gulp to auto-refresh the web browser whenever we change html/css. Also view & control webpage from multiple devices on same wifi (mobile, tablet, laptop)

**1.** Gulp watch `npm install gulp-watch --save-dev`

**2.** BrowserSync package `npm install browser-sync --save-dev`

**3.** Update *gulpfile.js* 
```
var watch = require('gulp-watch'),
browserSync = require('browser-sync').create();
```

Updating the watch task:
```
gulp.task('watch', function() {

  browserSync.init({
    server: {
      baseDir: "app"
    }
  });

  watch('./app/index.html', function() {
    browserSync.reload();
  });

  watch('./app/assets/styles/**/*.css', function() {
    gulp.start(‘cssInject’);
  });
});
```
Adding cssinject task to *gulpfile.js*:

```
gulp.task('cssInject', ['styles'], function() {
  return gulp.src('app/temp/styles/**/*.css')
    .pipe(browserSync.stream());
});
```

**4.** Use the External IP to view and control webpage from all devices simultaneously. (Mobile, Tablet, Laptop, Desktop -Any device,Any browser - They just need to be on the same wifi)
  <img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/browsersyncdemo.PNG">

**5.** Maintainable gulpfile by putting tasks into *gulp/tasks* as separate files e.g. *watch.js*, *styles.js*
Edited *gulpfile.js* :

```
require('./gulp/tasks/styles');
require('./gulp/tasks/watch');
```

**6.** Gulp error handling for styles task, otherwise css syntax errors will cause browsersync/watch task to halt.

Edit *gulp/tasks/styles.js* :

```
gulp.task('styles', function() {
  return gulp.src('./app/assets/styles/styles.css')
    .pipe(postcss([cssImport, cssvars, nested, autoprefixer]))
    .on('error', function(errorInfo) {
	console.log(errorInfo.toString());
      this.emit('end');
    })
    .pipe(gulp.dest('./app/temp/styles'));
});
```
## Post-css mixins

Media queries for mobile responsiveness.
Start css with a mobile-first approach by adding baseline smallest screen size then add mixin mediaqueries for progressively larger screens.

**1.** Install mixin package
```
npm install postcss-mixins --save-dev
```

Edit partial *gulpfile.js* i.e, *gulp/tasks/styles.js*:
`mixins = require('postcss-mixins');`

and update pipe in same file:
`.pipe(postcss([cssImport, mixins, cssvars, nested, autoprefixer]))`

**2.** Create reusable mixin blocks in file *app/assets/styles/base/_mixins.css*
```
@define-mixin atSmall {
  @media (min-width: 530px) {
    @mixin-content;
  }
}

@define-mixin atMedium {
  @media (min-width: 800px) {
    @mixin-content;
  }
}

@define-mixin atLarge {
  @media (min-width: 1200px) {
    @mixin-content;
  }
}
```

Import this file in *styles.css* `@import “base/_mixins.css”;`

**3.** We can now use `@mixin [mixinName]` in stylesheets. Nest in selectors as follows:

```
.row{


	@mixin atMedium{
		  &__medium-4{
			    float: left;
			    width: 33.33%;
		  }
		  
		  &__medium-8{
			    float: left;
			    width: 66.66%;
		  }
	}

}

```

## Responsive Images
We use responsive images for two reasons:
1. Art direction (Using differently-cropped images depending on screen size.)
2. File size / resolution (Images with resolution/size appropriate to the user's screen are downloaded)

**1. "Art direction"**
Use the `<picture>` tag with media attribute:
```
<picture>
	<source srcset=“images/dog-crop-large.jpg” media=“(min-width: 1200px)”>
	<source srcset=“images/dog-crop-medium.jpg” media=“(min-width: 760px)”>
	<img src=“images/dog-crop-small.jpg” alt=“Puppy in the sand.”>
</picture>
```
<p align="center">
  <br><br>
<img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/our-start.jpg">
<img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/our-start-portrait.jpg">
<img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/our-start-landscape.jpg">
</p>

**2. Image resolution / file size**
Use `srcset`. The number after each image denotes the width of the image The browser/device uses this to determine which is the most appropriate to download, and doesn’t download the alternatives.
```
<img srcset=“images/dog-res-small.jpg 570w, images/dog-res-medium.jpg 1200w, images/dog-res-large.jpg 1920w” alt=“Puppy in the sand”>
```
<p align="center">
  <br><br>
<img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/testimonial-jane-hi-dpi-i.jpg">
<img src="https://github.com/Jyotsna-Singh/CheatSheets/blob/master/Modern-Dev-Workflow-Gulp-Node/testimonial-jane-i.jpg">
</p>
