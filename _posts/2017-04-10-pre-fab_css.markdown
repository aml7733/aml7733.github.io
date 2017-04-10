---
layout: post
title:  "Pre-fab CSS"
date:   2017-04-10 20:11:08 +0000
---


There's a mantra among programmers; "Don't reinvent the wheel."  Well, not just among programmers.  It's a pretty common phrase, but that doesn't mean it won't hold here.

## What is CSS?

CSS (Cascading Style Sheets) is a language applied to HTML that changes the way it is displayed.  Everything in an HTML document can have one or more classes, and one id.  The CSS assigns display settings based on the HTML object name, class, or id.  This can include font size, division boarders, margins, color; pretty much anything you could think of.  

It's a wonderfully useful tool, allowing incredibly specific display settings.  Each element can have a default style, which can be overridden by class, and again overridden by id.  Default styling is the fastest way to get an HTML document to look pretty.  Things like `<p>` tags with an automatic font style and height, or link text `<a>Link</a>` with that classic default blue text are usually default styles.  While possible to fabricate the CSS ourselves, someone else has done it for us!

## Ready-Made Style Sheets

Lucky you (and me), there are plenty of already-finished stylesheets that we can lift and place into our code.  Once appropriately incorporated into the code, you'll immediately see the difference.  As soon as the imported CSS files are read, the default styles will be applied to the css The default stylings might be a little bland, but it's better than the plain-text version of HTML that would otherwise pop up in the browser.  More specific styling is accesed with pre-determined class names, so the only editing we need to do to our app/website is to add 

Perhaps the most popular is [Bootstrap CSS](http://getbootstrap.com/css/).  It uses classnames for `<div>` tags and divides the screen into 12 equal parts (as well as hundreds of other class-name-styles).  The sections scale properly when viewed on small or large screens, so your initial layout is preserved.  

I have preferred recently [Semantic UI](https://semantic-ui.com/).  It works beautifully with JavaScript front-end, and uses jQuery to allow for 'behaviors'; intuitive and responsive JavaScript interfacing commands.  But if you're just looking for normal CSS styling, once incorporated into the asset pipeline (if you're using Ruby on Rails) it works the same as Bootstrap CSS.  Just add the class names you like to your HTML, and see the difference.
