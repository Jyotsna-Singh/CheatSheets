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

## Disclaimer
**1.** Cheatsheet is based on [Udemy - Git a Web Developer Job](https://www.udemy.com/git-a-web-developer-job-mastering-the-modern-workflow) course by [Brad Schiff](https://www.udemy.com/user/bradschiff/)

**2.** I am not affiliated to this course and wont be paid if you buy it. Just a student who loved this course and found it useful.

**3.** Readme structure inspired by [Adam Skuse's cheatsheet](https://github.com/AdamSkuse/cheat-sheets/blob/master/Node-gulp-frontend-dev.md)

## Index

[Fundamental Concepts](#fundamentals)

[Pre-requisites](#prerequisites)

[Initializing a new project](#initializing-a-new-project)

[BrowserSync](#browserSync)

[PostCSS Mixins](#postcss)

[Responsive Images](#responsive-images)

[Automatic Sprites](#automatic-Sprite)

[Object-oriented Javascript and Webpack](#oop-js-webpack)

[Babel](#babel)

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


## Automatic Sprites

Configure Gulp to automatically create an Icon Sprite. Make our site load faster for visitors

**1.** Install svg-sprite package `npm install gulp-svg-sprite@1.3.1 --save-dev`

**2.** In gulp/tasks create *sprites.js*
```
var gulp = require('gulp');
svgSprite = require('gulp-svg-sprite');

var config = {
  mode: {
    css: {
      render: {
        css: {
          template: './gulp/templates/sprite.css'
        }
      }
    }
  }
}

gulp.task('createSprite', function(){
  return gulp.src('./app/assets/images/icons/**/*.svg')
    .pipe(svgSprite(config))
    .pipe(gulp.dest('./app/temp/sprite/'));
});
```
**3.** Add to *gulpfile.js*`require('./gulp/tasks/sprites');`

**4.** Create folder & file *gulp/templates/sprite.css*. In the sprite.css file add the following (moustache template `{`)
```
{{#shapes}}
  .icon--{{base}} {
    width: {{width.outer}}px;
    height: {{height.outer}}px;
    background-image: url('/temp/sprite/css/{{{sprite}}}');
    background-position: {{position.relative.xy}};
  }
{{/shapes}}
```
**5.** Copy *sprite.css* file to *app/assets/styles/modules/_sprite.css* & Rename file to *_sprite.css* to match existing code

Install rename package `npm install gulp-rename --save-dev`

Edit *sprites.js*

`rename = require('gulp-rename');`

```
gulp.task('copySpriteCSS', ['createSprite'], function(){
  return gulp.src('./app/temp/sprite/css/*.css')
    .pipe(rename('_sprite.css'))
    .pipe(gulp.dest('./app/assets/styles/modules'));
});

gulp.task('icons', ['createSprite', 'copySpriteCSS']);
```

Add to *app/assets/styles/styles.css* `@import "modules/_sprite";`

**6.** Move svg files from temp folder to assets folder by Editing sprites.js

```
var config = {
  mode: {
    css: {
      sprite: 'sprite.svg',
      render: {
        css: {
          template: './gulp/templates/sprite.css'
        }
      }
    }
  }
}

gulp.task('copySpriteGraphic', ['createSprite'], function(){
  return gulp.src('./app/temp/sprite/css/**/*.svg')
    .pipe(gulp.dest('./app/assets/images/sprites'));
});

gulp.task('icons', ['createSprite','copySpriteGraphic', 'copySpriteCSS']);
```

Edit *sprite.css* to remove repetitive icon urls
```
.icon{
  background-image: url('/assets/images/sprite/{{{sprite}}}');
}

{{#shapes}}
  {{#first}}
    .icon{
      background-image: url('/temp/sprite/css/{{{sprite}}}');
    }
  {{/first}}
  .icon--{{base}} {
    width: {{width.outer}}px;
    height: {{height.outer}}px;
    background-position: {{position.relative.xy}};
  }
{{/shapes}}

```
Use sprite icons in *index.html* `<span class="icon icon--star"></span>`

**7.** Clean task to delete duplicate .svg files (e.g, if you delete one icon, the new sprite file will not replace the old one and create another version of the .svg file)

Install del package `npm install del --save-dev`

Updating *gulpfile.js* by creating beginClean task and adding it to `icons` task.
```
del = require('del');
gulp.task('beginClean', function(){
  return del(['./app/temp/sprite', './app/assets/images/sprites']);
});
```

End the clean task to delete temp sprite folder

```
gulp.task('endClean', ['copySpriteGraphic', 'copySpriteCSS'], function(){
    return del('./app/temp/sprite');
});
```
## Object-oriented Javascript and Webpack
Blueprint in JavaScript (classes in other OOP languages). ECMA5 way of creating "classes". Later, after installing Babel, we can use the ECMA6 class constructor 
```
function Person(fullName, profession) {
this.name = fullName;
this.profession = profession;
this.greet = function() {
	console.log(“Hi, my name is “ + this.name + “ and I am a “ + this.profession “ .”;
	}
}

var jyo = new Person(“Jyotsna Singh”, “Fullstack Developer”)
jyo.greet();
```
JS doesn’t have a native ‘require’ function. We can use Webpack to allow us to store class constructors etc in separate .js files i.e. make it modular.

**1.** Create: `app/assets/scripts/App.js` `app/assets/scripts/modules/`

Modules (e.g. Person.js) will go in the modules/ folder. Then, require them at the top of App.js e.g. 
`var Person = require(‘./modules/Person’);`

Webpack will compile all the js modules into a single file that the browser can then read.

**2.** Install webpack globally `npm install webpack -g`

**3.** Create *webpack.config.js* in the project root folder
```
module.exports = {
		 entry: __dirname + "/app/assets/scripts/App.js",
		 output: {
		 path: __dirname + "/app/temp/scripts",
		 filename: "App.js"
	 }
}
```

**4.** Run `webpack` in node.js command prompt

**5.** Update path to script file in index.html to point to assets/temp/scripts/App.js

Each js module (e.g. Person.js) will need an export line at the end, so that Webpack knows what to do with it. 
`module.exports = Person;`

**6.** Webpack can also require third-party modules such as jquery.
If using jquery in project, first install it with `npm install jquery --save`. Then, in each module that uses jquery, at the top put `var $ = require('jquery');`

<p align="center">
<img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/webpack.png" width="500px" height="auto">
</p>

### Integrate Webpack in Gulp Automation  

Browsersync will automatically update if a .js file is edited:

**1.** Install webpack locally `npm install webpack --save-dev`

**2.** Create *gulp/tasks/scripts.js*

**3.** Edit *gulpfile.js* by adding `require(‘./gulp/tasks/scripts’);`

**4.** Add the following to *gulp/tasks/scripts.js*
```
var gulp = require(‘gulp’),
webpack = require(‘webpack’);

gulp.task(‘scripts’, function(callback) {
	webpack(require(‘../../webpack.config.js’), function(err, stats) {
		if (err) {
			console.log(err.toString());
		}
		console.log(stats.toString());
		callback();

	});
});
```

**5.** In watch.js, after 'css' and 'watch' tasks, add:
```
watch(‘./app/assets/scripts/**/*.js), function() {
	gulp.start(‘scriptsRefresh’);
})

gulp.task(‘scriptsRefresh’, [‘scripts’], function() {
	browserSync.reload();
)};
```

Now, webpack will compile a js file for the browser to use from our main file and modules into App.js in the temp folder; and browserSync will automatically update the browser when any js files are edited. If there are any errors it will throw them up without causing browsersync to end.


## Babel
<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/babel.png" width="500px" height="auto"/>
</p>
 Babel enables us to write ES6 code, which it then converts to ES5 code to ensure browser compatibility.
 
**1.** Install Babel packages `npm install babel-core babel-loader babel-preset-es2015 --save-dev`

**2.** Edit *webpack.config.js* so the whole thing reads as follows. Webpack will run the code through Babel before creating the dist version of App.js.
```
module.exports = {
	entry: “./app/assets/scripts/App.js”,
	output: {
		path: “./app/temp/scripts”,
		filename: “App.js”
		},
		modules: {
			loaders: [
				{
					loader: ‘babel’,
					query: {
						presets: [‘es2015’]
					},
					test: /\.js$/,
					exclude: /node_modules/
					}
				]
			}
}
```
### ECMA6 refactor - imports / exports

Additionally, as ECMA6 supports importing from external .js files, in *App.js* we can replace

`var Person = require(‘./modules/Person’);` with `import Person from ‘./modules/Person’;`

and in *Person.js* replace

`module.exports = Person;` with `export default Person;`

## Lazy loading images

**1.** `npm install lazysizes --save`

**2.** create *Vendor.js* in same dir as *App.js* and add line `import 'lazysizes';`

**3.** In *webpack.config.js* edit 'entry' and 'export' properties to following:
```
module.exports = {
	entry: {
			App: “./app/assets/scripts/App.js”,
			Vendor: “./app/assets/scripts/Vendor.js”
		},
	output: {
		path: “./app/temp/scripts”,
		filename: “[name].js”
		},
		modules: {
			loaders: [
				{
					loader: ‘babel’,
					query: {
						presets: [‘es2015’]
					},
					test: /\.js$/,
					exclude: /node_modules/
					}
				]
			}
}
```

**4.** in head of *index.html* add `<script src=“/temp/scripts/Vendor.js”></script>`

**5.** To set an image to lazyload, add the class 'lazy-load' and change 'src'/'srcset' to 'data-src'/'data-srcset'. e.g.:

`<img class=“lazyload” data-srcset=“image1.jpg 160w, image2.jpg 320w”>`

**6.** For background images, add 'lazyload' class to the html element. Then in the css assign the background image in a 'lazyloaded' class. This class will be added to the html element when the window scrolls close to the element. e.g.

```
.testimonials {
	&.lazyloaded {
		background: url(/assets/images/background.jpg) top 			center no-repeat;
		background-size: cover;
	}
}
```

## Preparing files to go live

**1.** create *dist* folder

**2.** Install imagemin for image compression
`npm install gulp-imagemin --save-dev`

Install del so we can delete old files when creating a new build
`npm install del --save-dev`

**3.** create *gulp/tasks/build.js*

#### Process images

**1.** Add following to *gulp/tasks/build.js*

```
var gulp = require('gulp'),
imagemin = require('gulp-imagemin');

gulp.task('optimizeImages', function() {
  return gulp.src("./app/assets/images/**/*")
  .pipe(imagemin({
    progressive: true,
    interlaced: true,
    multipass: true
  }))

  .pipe(gulp.dest("./dist/assets/images"));
});

gulp.task('build', ['optimizeImages']);
```

**2.** In *gulpfile.js* add `require(‘./gulp/tasks/build’);

**3.** Add 'deleteDistFolder' task to *build.js* to clear out dist folder before each new build

```
var gulp = require('gulp'),
imagemin = require('gulp-imagemin'),
del = require('del'); //so we can delete the dist folder at start of each build

gulp.task('deleteDistFolder', function() {
  return del("./dist");
});

gulp.task('optimizeImages', ['deleteDistFolder'], function() {
  return gulp.src("./app/assets/images/**/*")
  .pipe(imagemin({
    progressive: true,
    interlaced: true,
    multipass: true
  }))

  .pipe(gulp.dest("./dist/assets/images"));
});

gulp.task('build', ['deleteDistFolder', 'optimizeImages']);

```
N.B. 'deleteDistFolder' has been added as a dependency in the last line.

#### Process CSS and Javascript with Usemin
We want to
-copy to dist folder
-compress
-revision (make unique filename that forces browsers that have cached our page to d/load new versions)

**1.** `npm install gulp-usemin —save-dev`

**2.** add to *build.js* so it looks like following:
```
var gulp = require('gulp'),
imagemin = require('gulp-imagemin'),
del = require('del'), //so we can delete the dist folder at start of each build
usemin = require('gulp-usemin');

gulp.task('deleteDistFolder', function() {
  return del("./dist");
});

gulp.task('optimizeImages', ['deleteDistFolder'], function() {
  return gulp.src("./app/assets/images/**/*")
  .pipe(imagemin({
    progressive: true,
    interlaced: true,
    multipass: true
  }))

  .pipe(gulp.dest("./dist/assets/images"));
});

gulp.task('usemin', ['deleteDistFolder'], function() {
  return gulp.src("./app/index.html")
  .pipe(usemin())
  .pipe(gulp.dest("./dist"));
});

gulp.task('build', ['deleteDistFolder', 'optimizeImages', 'usemin']);
```

**3.** So that the dist version of *index.html* points to the correct, dynamically-named versions of the CSS and JS files, wrap the references in comments as follows:
```
<!-- build:css assets/styles/styles.css -->
<link rel="stylesheet" href="temp/styles/styles.css">
<!-- endbuild -->
```
```
<!-- build:js assets/scripts/App.js -->
<script src="assets/scripts/App.js"></script>
<!-- endbuild -->
```

**4.** run `gulp build`
this will create index.html in dist folder with usemin comments removed, and create script and css files in appropriate dist subfolders.

#### Compression and versioning

**1.** `npm install gulp-rev gulp-cssnano gulp-uglify --save-dev`
(gulp-rev revisions files; gulp-cssnano compresses css; gulp-uglify compresses javascript)

**2.** at top of *build.js* add:
```
rev = require('gulp-rev'),
cssnano = require('gulp-cssnano'),
uglify = require('gulp-uglify');
```

**3.** Update 'usemin' task:
```
gulp.task('usemin', ['deleteDistFolder'], function() {
  return gulp.src("./app/index.html")
  .pipe(usemin({
    css: [function() {return rev()}, function() {return cssnano()}],
    js: [function() {return rev()}, function() {return uglify()}]
  }))
  .pipe(gulp.dest("./dist"));
});
```
NB If you're using ECMA6 syntax (e.g. arrow functions) in your JS and are not using Babel, uglify will throw an error.

**4.** Add a previewDist task to *build.js* that will let us preview our dist files using Browsersync:

```
var gulp = require('gulp'),
imagemin = require('gulp-imagemin'),
del = require('del'), //so we can delete the dist folder at start of each build
usemin = require('gulp-usemin'),
rev = require('gulp-rev'),
cssnano = require('gulp-cssnano'),
uglify = require('gulp-uglify'),
browserSync = require('browser-sync').create();

gulp.task('previewDist', function() {
  browserSync.init({
    notify: false,
    server: {
      baseDir: "dist"
    }
  });
});
gulp.task('deleteDistFolder', function() {
  return del("./dist");
});

gulp.task('optimizeImages', ['deleteDistFolder'], function() {
  return gulp.src("./app/assets/images/**/*")
  .pipe(imagemin({
    progressive: true,
    interlaced: true,
    multipass: true
  }))

  .pipe(gulp.dest("./dist/assets/images"));
});

gulp.task('usemin', ['deleteDistFolder', 'styles'], function() {
  return gulp.src("./app/index.html")
  .pipe(usemin({
    css: [function() {return rev()}, function() {return cssnano()}],
    js: [function() {return rev()}]
  }))
  .pipe(gulp.dest("./dist"));
});

gulp.task('build', ['deleteDistFolder', 'optimizeImages', 'usemin']);
```
note that  styles was added as a dependency of usemin. if we had a scripts task, as in the original tutorial, this would also be added as a dependency here.

#### Copying other files to our dist folder with build
**1.** Add the following to *build.js*:
```
gulp.task('copyGeneralFiles', ['deleteDistFolder'], function(){
  var pathsToCopy = [
    './app/**/*',
    '!./app/index.html',
    '!./app/assets/images/**',
    '!./app/assets/styles/**',
    '!./app/assets/scripts/**',
    '!./app/temp',
    '!./app/temp/**'
  ]

  return gulp.src(pathsToCopy)
  .pipe(gulp.dest("./dist"));
});
```
**2.** Update build task at end of same file:
```
gulp.task('build', ['deleteDistFolder', 'copyGeneralFiles', 'optimizeImages', 'usemin']);
```
