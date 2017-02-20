---
layout: post
title:  "Rails Project Mode"
date:   2017-02-20 07:38:45 +0000
---


I had a good time with this project.  It was fun to flex the "magic" of rails without any reigns.  The generators are powerful, the conventions fairly obvious, and that meant I was able to create a fully functioning rails app with some cool association features in about a day and a half.  I had been warned against the rails scaffold generator because of all the additional files it created that would go unused.  Although, any generator that added a js file or coffee was wasted on me.  I guess I haven't gotten that far in my development learning.  

It was easy to map my routes, and any time I was confused, `rake routes` to the rescue.  Full list of all the routes, and which controller they use, and what action they're mapped to.  Even lists the path nicknames (new_user_session, edit_post, etc).

Devise makes user authentication a cinch, so long as you don't mind not knowing what's going on under the hood.  That bothered me, but not enough to re-do it myself.  And I found a straight-forward guide on working with devise and omniauth together at: [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-configure-devise-and-omniauth-for-your-rails-application).  Full disclosure though, I still haven't figured out the omniauth issues.  I'm running into problems allowing my app to receive redirects from my rails server (running Learn IDE on a Windows machine, I get a different address each time I close and re-open my computer).

And man-o-man, did I save a lot of debugging time when I realized that a `binding.pry` would work in my console while the rails server was running, so I could actually attempt CRUD actions manually and read the params returned immediately.  That helped me with some typos in my strong parameters (items_attributes was returned, and i had permitted item_attributes).

I tried to make full use of rendering partials (particularly forms), and my favorite tool so far, the form_for builder.  It links a form in the views directly to an instance of a model object.  It can automatically update the values of the form with the object's attributes (and name the input fields appropriately in the rendered view), and it knows which HTML verb to use when submitting the data (post vs patch/put).  Basically, it means I can make a single form to create and edit an object, and all those fields are automatically surrounded by an error field div if the data entered isn't valid (assuming you render the same form with the same instance of the object).  Very convenient.


