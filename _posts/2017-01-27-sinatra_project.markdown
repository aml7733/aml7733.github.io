---
layout: post
title:  "Sinatra Project"
date:   2017-01-27 21:24:44 +0000
---


I figure this time I'll write as I go, rather than just summing up the process after I'm done with the project.  That means the post here will seem a little jumpy, as I'll be discussing decisions and making decisions instantaneously (from the reader's perspective). It'll be interesting, here goes:

## Idea time

First thing's first.  Can't start coding until I have an idea.  My initial thought was to make an 'owned movie' database app.  User could log in, create new movies, label them with actors, directors, and type (dvd, bluray, digital download, etc.), and the main crux of the app would be the search functions (by actor, director, or type).

Another idea: my brother is a rowing coach.  I thought he might be able to use a web app to assign rowers to boats.  Coach has many boats, boats have many rowers. Coach should have the account/login info and is the only person able to edit the boats, but the rowers need to be able to see which boat they're in, so that would affect the show action.  The more I write about this one, the more interesting it becomes.  I'm definitely going with the crew app.


## App Code

Ok, so I've set up my associations as follows: Coach has many boats, boat has many rowers, coach has many rowers through boats.  I want to be able to create new boats, then add rowers to them.  Only the coach that's logged in may edit the boats.  


The read aspect is pretty simple. I just had to make sure to make helper methods in my application controller (the lessons say that it's bad form to put too much ruby in the .erb view files. Just have to make sure to check if a Coach is logged in first.  The coach will be redirected to a read/edit page, and anyone else will just see all the boats available and the associated rowers.


Simple 'post' processes and accurate formation of the naming of the form inputs allow me to simply use activerecord's update method on the boat object.

And sorry, whomever is grading this thing, but I uploaded the walkthrough before I saved the delete boat button.  But I promise it works now.  

## Possible future capabilities
I've left in weight and power attributes for each rower.  In the future, i'd like to be able to aggregate the weight of the boat (including the rowers), and maybe develop some algorithm for the 'boat speed factor' for each rower.  The power attribute could be weighed (pardon the pun) against the additional weight of the rower to see if he/she would make a certain boat faster or slower.
