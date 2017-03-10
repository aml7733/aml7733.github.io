---
layout: post
title:  "Setting Up a Javascript Front End for a Rails App"
date:   2017-03-09 22:39:59 -0500
---


First thing's first, if you haven't already, run `rails new <app name>` .  That will generate a ton of files (not all of which are needed for every scenario, but that's for you to decide).  The Rails Asset Pipeline is implemented via the gem 'sprockets-rails'.  For JS setup, look into the `assets/javascripts` auto-generated folder. 

My favorite aspect of rails is the pre-loaded help you get with most of the auto-generated files.  Many files that come with rails include commented text that explains most everything you need to know.  It even included a url to the Sprockets README on github.  The JS manifest file, called `application.js` in the javascripts folder, has a few lines describing how to use the mainfest.  The pipeline (more specifically, the sprockets gem) will concatenate all the js files to a single file, allowing for faster load times.  (It'll do the same for your css files.) All you've got to do is write the file and put it in the correct folder.  The manifest already includes the line `//= require_tree .`, which will include any js file in `app/assets/javascripts`, `vendor/assets/javascripts`(for any foreign libraries you want to include), or `lib/assets/javascripts`(for scripts that might not be in the app scope).

The asset pipeline is set up to be able to handle coffeescript, so use at your discretion.  It's a neat little language that compiles into JS one-to-one.  That is, no interpretation at runtime. It's basically syntactical sugar.  A little easier to read, and code that's easy to read is code that's easy to update.  The manifest also includes the jquery library by default, which I highly recommend.

After the initial setup, all that's left is to write your scripts.  I highly recommend starting off the file with a $(document).ready() statement, so you're sure everything's loaded before the script runs.  Beyond that, it's all up to you.
