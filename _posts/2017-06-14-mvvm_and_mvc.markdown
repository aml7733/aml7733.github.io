---
layout: post
title:  "MVVM and MVC"
date:   2017-06-14 05:52:51 +0000
---


## Model View Controller

The 'classic' Model-View-Controller is a way to separate the connected aspects of a web app, so as to make the app more easily editable by other programmers.  "Separation of the concerns" as it's said, allows others (or yourself) to edit a single piece of code, and not worry so much about breaking things down the line.

Rails is an example of a MVC framework which allows "out of the box" models, views, and controllers.  The model contains any data, logic, or rules that are completely independent of the user interface.  That is database definitions, authentication, and saving/editing/deleting from the database, etc.  The view contains the user interface, which allows the user to enter/edit/delete information that is presented on the client side.  And finally the controller communicates between the two; it queries the models for data, organizes it, and presents to the view.

## Model-View-ViewModel

The model and view in this framework function much the same way.  The view still shows data to the user, and the model still contains the "background logic."  MVVM's even have a controller often times.  The difference is the ViewModel, which represents the state of the data in the view.  Statefullness allows faster communication, since data is cached on the client side.
