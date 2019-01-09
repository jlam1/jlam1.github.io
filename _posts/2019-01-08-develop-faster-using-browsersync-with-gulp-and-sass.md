---
layout: post
title: Develop faster using browsersync with gulp and sass
tags: [browsersync, gulp, sass, css, html, bootstrap, node, frontend, tutorial, development]
---

## Overview
This is a small guide for developing on the frontend more quickly using an automation tool call browsersync.
I will go over how I personally build websites from a design to static page.
In a nutshell, [BrowserSync](https://www.browsersync.io/) is an opensource automation tool built with Nodejs that has features such as file syncs and network throttling for testing and many more.

## Setup
Before we start install nodejs then initialize the project by running

{: .box-note}
npm init

This will prompt you questions about the project's name, version, etc. Press Enter for default values.
This will create a `package.json` file in the root. This is where you can see all dependencies installed and change their versions for whatever reasons.

This is my usual setup for folder structure.
![folderstructure](https://johnjlam.com/img/posts/2019-01-08/folderstructure.PNG)

And in my index file this is what I usually start with.

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Document</title>

	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS"
	 crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css?family=Roboto" rel="stylesheet">
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.css">
	<link rel="stylesheet" href="css/styles.css">

</head>

<body>
	<main>
		<h1>HELLO WORLD!</h1>
	</main>

	<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js" integrity="sha384-wHAiFfRlMFy6i5SRaxvfOCifBUQy1xHdJ/yoi7FRNXMRBu5WHdZYu1hA6ZOblgut"
	 crossorigin="anonymous"></script>
	<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k"
	 crossorigin="anonymous"></script>
	<script src="js/main.js"></script>
</body>
</html>
```

## Installing Packages and Gulp Tasks
Input these commands into the terminal/command line

{: .box-note}
npm install --save -g browser-sync

{: .box-note}
npm install --save -g gulp

{: .box-note}
npm install --save -g gulp-sass

In the root of your project create an empty javascript file name `gulpfile.js` with these lines

```javascript
var gulp = require('gulp');  
var sass = require('gulp-sass');  
var browserSync = require('browser-sync');

gulp.task('sass', function () {  
    gulp.src('scss/styles.scss')
        .pipe(sass({includePaths: ['scss']}))
        .pipe(gulp.dest('css'));
});

gulp.task('browser-sync', function() {  
    browserSync.init(["css/*.css", "js/*.js"], {
        server: {
            baseDir: "./"
        }
    });
});

gulp.task('watch', ['sass', 'browser-sync'], function () {  
    gulp.watch("scss/*.scss", ['sass']);
    gulp.watch("*.html").on('change', browserSync.reload);
});
```

## Test
Create an empty scss file inside the scss directory.
Run the command in the terminal

{: .box-note}
gulp watch

This should start on your localhost:3000.

Input a valid scss into the file and save. This will compile the scss file into the css directory into valid css syntax.

Example:
![folderstructure](https://johnjlam.com/img/posts/2019-01-08/taskrunner.PNG)

## Issues
There is an issue (as of this post's date), when running the command `gulp watch`, it will mention that the `Task function must be specified`.

You can resolve this by going in `package.json` and change the gulp's version to 3.9.1. Afterwards run `npm install`.

```json
{
  "name": "frontend_template",
  "version": "1.0.0",
  "description": "",
  "main": "gulpfile.js",
  "dependencies": {
    "browser-sync": "^2.26.3",
    "gulp": "^3.9.1",
    "gulp-sass": "^4.0.2"
  },
  "devDependencies": {},
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

## Sources
* [BrowserSync](https://www.browsersync.io/)
* [Gulp](https://gulpjs.com/)
* [Sass](https://sass-lang.com/)
* [Nodejs](https://nodejs.org/en/)