---
layout: post
title: Develop faster using browsersync with gulp and sass
tags: [browsersync, gulp, sass, css, html, bootstrap, node, frontend, development, tutorial, vscode]
---

## Overview
This is a small guide for developing on the frontend more quickly using an automation tool call browsersync.
I will go over how I personally build websites from a design to static page using html and sass.
In a nutshell, [BrowserSync](https://www.browsersync.io/) is an opensource automation tool built with Nodejs that has features such as file syncs and network throttling for testing and many more.

## Before you start
* Text Editor Tool (using Visual Studio Code)
* Installation of Nodejs

## Setup
Before we start initialize the project by running
{: .box-note}
npm init

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

## Installing Packages
Install browser-sync with this command
{: .box-note}
npm install --save -g browser-sync

Install gulp using this command 
{: .box-note}
npm install --save -g gulp



## Sources
* [BrowserSync](https://www.browsersync.io/)
* [Gulp](https://gulpjs.com/)
* [Sass](https://sass-lang.com/)
* [Nodejs](https://nodejs.org/en/)