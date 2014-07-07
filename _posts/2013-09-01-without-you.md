---
title: Can We Live Without You?
layout: post
created_at: Mon Sep 01 2013 17:50
permalink: /2013-09-01-without-you
author: inchworms
twitter: inchworms_
---

Today we moved from the 5th floor offices of [TravisCI](https://twitter.com/travisci) to the 5th floor offices of [Co-Up](https://twitter.com/co_up). We cried, but not from all the stairs we had to climb. We cried because we didn't wanna say goodbye :-(

![crying](http://24.media.tumblr.com/tumblr_m87b30INY21r0uywso1_500.gif)

But, as they say, when one door closes, another one opens. Pretty soon our new desk was set up, our coach Urs had assigned us several challenging tasks, and, along with Urs' colleague Adam, shared a delicious salad for lunch.

![before](/images/before.jpg)
![after](/images/after.jpg)

Mostly today was spent working on setting up a rake task that would create a seperate database we will use to test the performance of our data viz appliaction. Because we wanted our rake task to: look for a performance test database, delete it if there was one, then/or create a new performance test database - we had to work out how we could access (unix) system commands and which ones would return something we could use to check the presence of the performance test db. This took AGES.

Tomorrow we're going to look at caching the contents of one of our (small) tables locally to improve performance further.



