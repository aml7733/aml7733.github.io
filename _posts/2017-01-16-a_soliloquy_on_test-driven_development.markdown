---
layout: post
title:  "A Soliloquy on Test-Driven Development"
date:   2017-01-16 16:11:53 +0000
---

I totally understand test driven development.  Really, I do.  It ensures the program functions exactly to specifications, no more (which would be wasteful) and no less (which wouldn't work).  It's easier to teach, easier to pass, and explicit in nature, assuming the tests are well-designed.  I'm not 100% sold however.  But in order to determine why, I'll start with the pro's:

## Pro TDD:
Debugging is less daunting, because the code (conceptually, at least) is being written to pass the tests directly.  It inherently inspires confidence; not only because the initial failed tests are *expected*, but each passed test carries the weight of accomplishment.  I was once told that it "allows us to use more of our brainpower on the development, rather than splitting work on writing code and getting the desired result."  The most noticeable 'pro' is that it closely resembles the type of development I imagine I'll see in a web dev job.  And it allows easier group work, if all the outputs and tests are spelled out first.

## Anti TDD (for me, at least)
It's great that TDD inspires confidence, but I don't need that.  I get a perfectly acceptable sense of accmomplishment without the green text telling me I did a good job.  And as for the 'split brain power' thing, it's a notion I reject out of hand.  First off, 'brain power' isn't finite.  And even if it were, forcing me to write all the tests I want to pass first just wastes time for me.  Although the worst part, especially at this point in my learning process, is that TDD is not designed for learning new concepts.  Here on Learn.co, the tests vary from lab to lab, even when dealing with the same concepts.  For example: the name="" attribute for an input field on an HTML form; I went through a full lesson detailing how we should name these such that the params hash posted can be easily manipulated, and the tests on the following lab completely ignored this lesson.  I go from a test that requires "User.create(params[:user])" to a test that requires "User.create(:username => params[:username], :email => params[:email], :password => params[:password])", and I HAVE to do it this way because of how the tests are written.  It wastes hours.

## Just let me code!
Again, I understand why this process is taught.  It can be especially useful for an online-only teaching curriculum, because the school doesn't have to hire nearly as many people to grade work.  Just keep trucking along until all those tests turn green, then hit submit!  But at the expense of the hours and hours of frustration at varying tests, I'll just figure it out myself, thanks.
