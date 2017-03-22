---
layout: post
title:  "Full Stack"
date:   2017-03-21 18:38:22 -0400
---


The time has come.  I'm finally done.  I took a blank file and made a rails back-end with serialization and an ActiveRecord database.  Then I took another blank file and made a React/Redux front-end.  

I learned a ton, including perhaps the most important lesson so far in my coding: there's always a newer version coming.  I was barely comfortable with react-router (v3.0.2), when it was completely overhauled for version 4 right after I finished the routing section.  I ended up sticking with v3 for the project, but I'm excited to learn the new one once I have a little more time on my hands.

## React

React is a fairly intuitive framework.  Once I realized (ie, read someone else's realization) that it's just a view framework, things started to make a little more sense to me.  The component system is just a way to extrapolate logic I might want to put in the view.  It offers simplicity:

`import React, { Component } from 'react';
import { Link } from 'react-router';

class App extends Component {

  render() {
    return (
      <div className="App">
        <h2 className="ui block header">Welcome to Budge</h2>
        <ul className="nav">
          <li><Link to="/items">Show All Items</Link></li>
          <li><Link to="/items/new">Add New Item</Link></li>
        </ul>
        {this.props.children}
      </div>
    );
  }
}

export default App;`

This is the entire component for my container app.  Now, it's only able to be this simple because most of that logic is extrapolated to index.js.


# Redux
There was certainly some complexity to the redux middleware.  It took a fair amount of trial and error, as well as plenty of documentation, to get a solid foundation.  What it lacks in simplicity, it makes up for in scalability.  Not particulary useful to me with this app, but will certainly be useful when I make larger apps in the future.  Redux took the api calling out of the components and allowed for a single place to host everything that needed back end access.

It hosted a separate `store`, which housed data that could be put into a component's `state`.  So instead of using extra memory to have a state for each component, only one instance of that data is accessed by anything that needs it.

I used `fetch().then()` to make api calls to make asynchronous calls, so the components loaded correctly afterward.

# Rails
I spent a lot of time in the Rails part of the curriculum, so the back end was comfortable.  I took the api calls, created (or deleted) an object and saved it to an ActiveRecord database.  Then I serialized it into JSON and returned it to the front end.  


# TL,DR:

Redux used the JSON representation from the Rails database to add data to a store, and the redux components (which needed access to the store) used a function to map that data to their properties.  Back end data, front end visuals.
