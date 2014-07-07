---
title: Getting Our Hands Dirty with Tests
layout: post
created_at: Mon Jul 15 2013 17:49
permalink: /2013-07-15-dirty-tests
author: inchworms
twitter: inchworms_

---

So today, after posting an introduction to ourselves on the [RGSoC Blog](http://railsgirlssummerofcode.org/blog/introducing-inchworms/), we started building another version of our Songs by Nancy app, but this time using Test Driven Development (TDD).

RGSoC Team [Hackety Hack](http://teamhackety.wordpress.com/2013/07/14/the-importance-of-testing/) wrote a great post last week about the importance of testing. Part of our plan for RGSoC was to learn more about testing within the Sinatra development enviroment. To do this we will (for starters) build our Songs by Nancy app again starting with tests first.

Understanding the importance of TDD is one thing. Knowing what to test for is another. After Matt gave us a few pointers about how we could go about deciding that, we watched a couple of videos, including a tutorial with some basic examples of using Rspec with Sinatra, we started building v3 of our app, starting with some tests.

Everything went okay (and by 'everything' we mean a single test) until we wanted to test the content of a view. As usual there was an inordinate amount of mostly fruitless searching online for help. But (also as usual) we eventually found something to [help us](https://github.com/jnicklas/capybara). We learnt that Sinatra doesn't respond to the same Rspec methods that Rails does, and that in any case, to test anything on the front-end of our app we would need to use the Capybara gem. Capybara helps test web applications by simulating how a real user interacts with the app (and an app's views function in response to a user's interaction, hence the need for Capybara when testing views).

So, it's been a long day, and now we're off to our Rubymonsters project group.

![capybara](http://www.symbolicsound.com/zzz/pub/Learn/Capybara/Cc-Capybara.gif)
