---
layout: post
title: How to run CodeIgniter and MySQL using XAMPP
tags: [codeigniter, php, sql, phpmyadmin, xampp, tutorial, development, walkthrough]
---

## Overview
A small tutorial on how to setup a project using the codeigniter framework by hosting it locally using xampp (which comes with apache, php, and mariaDB).

## Steps
1. Download [XAMPP](https://www.apachefriends.org/index.html) and run through the entire installation. Make sure to install xampp anywhere but the program files (they will prompt you so don't worry).

2. Go into the folder directory, in my case I have it installed in the root of my local disk `C:\xampp`

3. Download [CodeIgniter](https://codeigniter.com/) and traverse into `C:\xampp\htdocs`, create a folder for your project, and extract codeigniter files into it.
![codeigniterfolder](https://johnjlam.com/img/posts/2019-01-03/codeigniter_folder.PNG)

4. Run the XAMPP software in administrator mode and tick the boxes for both `Apache` and `MySQL` services.
![codeigniterfolder](https://johnjlam.com/img/posts/2019-01-03/xampp_settings.PNG)

## Test
To test open up your browser and input the url `http://localhost/`
This should reroute you to XAMPP's dashboard.
Afterwords try `http://localhost/codeigniter/` or the folder name that was created in the directory `htdocs`.

If successful it should look something like this:
![codeigniterfolder](https://johnjlam.com/img/posts/2019-01-03/codeigniter_index.PNG)

Go to `http://localhost/phpmyadmin/` to test whether or not phpmyadmin is setup correctly.

## Sources
* [CodeIgniter](https://codeigniter.com/)
* [CodeIgniter Documentation](https://codeigniter.com/user_guide/)
* [XAMPP](https://www.apachefriends.org/index.html)