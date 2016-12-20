---
layout: post
title:  "CLI App Project"
date:   2016-12-20 06:38:52 +0000
---


I liked the challenge of this one.  It was the first part of the Web Dev course that didn't have a framework to start.  It took me a little while to figure out how to set up the environment, bundler, gems, etc.  But once I got all that settled, it was smooth sailing.

## The Movie Game
If you're not familiar with the movie game, then your childhood was very different than mine.  You start with an actor or actress, and the next person has to name a movie they've been in, and the next has to name a different actor in the movie, et cetera.  You can't repeat, and if you take too long you get a strike.  Three strikes and you're out, of course.  My lunchtime friend group played so often, we sometimes struggled to even think of a starting actor, with such a variety of options.  Eventually one of us found the Internet Movie Database's 'Born Today' section.  Now, we'd start with a birthday wish: Happy birthday, Jake Gyllenhaal => Donnie Darko => Drew Barrymore => ...

And that, in turn, gave me the idea for my CLI app.  I take the imdb.com/date page and return a list of actors celebrating a birthday on the current date.  Then, of course, drill down into each actor for further profile page info.

## The app
The first thing to handle was finding the appropriate url for scraping.  Luckily, in addition to the widget on imdb's home page (which I wanted to avoid, too likely it would move or change in some way and break my scraper) they have a static date page, http://imdb.com/date which points to the individual current day page.  Unfortunately, it appeared that page was populated automatically because much of the text was free-standing (harder to find deliberately with css tags).  But fortunately, it became very convenient to store the string of today's date ("December 19") as a Scraper class variable, :today.

## Code
I started with the Actor class.  I initially struggled naming it because I knew the list would be populated with writers, producers, directors, etc. in addition to actors, but decided the simplicity was worth my dissatisfaction.  The attribute accessors were simple enough, I just made one for each of the attributes I needed.  Name, year, (the day would always be the same), profile_url, occupations, known_for, and bio_intro.  I initially included a trivia item, but it malfunctioned for lesser-known actors (if nobody listed a trivia fact, the box didn't exist).

I wanted to initiate the Actor with a name, year, and profile url, and make it push itself into @@all, so I could iterate through @@all and output a string for each.  Then I'd only need one line: `puts "#{self.name} was born today, #{Scraper.today}, #{self.year}` to make the initial list.  

That meant I needed the initial scrape of the date page to return a hash with attribute keys and string values.  I'm sure there's something really complicated to scraping (the lessons here on Learn all mention that it's difficult and I shouldn't get frustrated), but I think it's easy enough.  Once I understood how to use open-uri and Nokogiri to create a searchable and iteratable (? iterable?  feels like there's a word there) document, the css tags made it very simple to find the text I needed.  The real trouble lied with getting the text to look pretty.

I feel bad about how messy it looks, but it's not that tough to read through.  I searched for popular solutions to similar problems, and the quickest way I found to get rid of a bunch of whitespace is to .split and .join(" ") the text back together.

Once I was able to parse the site into the strings I wanted, I used a literal hash construct to make a hash with the same keys as the Actor class has attr_accessors (:name, :year, etc), and output an array of those hashes.  Back in the Actor class, I made a #create_from_array function, which literally defined the name, year, and profile url of a new Actor object to the passed argument hash.

It seemed wasteful to add the profile page info to every actor, so I organized my methods to only scrape the profile page after the actor was selected (by name).  It seems to work great now, although I'm sure my eyes will be opened for me in the assessment.

## Use

I know it's bare-bones, and I know there's not a lot of use for an app like this.  But I made it.  And it works.  And it'll work tomorrow, with a completely new set of actors.  So now I don't even need a browser to start off the movie game.  Just a simple `ruby actor-birthday-cli-project/bin/run.rb`, and I've got my pick of the litter.
