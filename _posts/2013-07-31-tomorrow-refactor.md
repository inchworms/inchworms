---
title: Drink and Be Merry for Tomorrow We Refactor
layout: post
created_at: Wed Jul 31 2013 16:12
permalink: /blog/2013-07-31-tomorrow-refactor
author: inchworms
twitter: inchworms_

---

Today we finished off the first iteration of rspec tests for Sinatra GET requests. This amounted to almost [100 different tests](https://github.com/inchworms/sinatra_tests/issues/3). Not bad for Sinatra newbies :-)

So far we've mainly just rewritten the existing Unit tests, turning them into RSpec versions. This has helped us get our heads around the differences between Unit and RSpec, and also enabled us to work out what Sinatra itself does with the various possible GET requests it can receive.

We've known all along that we would need to refactor our work. And not just because of messages like these:

![refactor](/images/refactor.png)

So today we're celebrating the fact that we're at the end of the GET list.

Tomorrow we begin refactoring, which we think will probably involve a bit of this:

![lower expectations](http://31.media.tumblr.com/5daa5eef61cfa2ffe7deac92a5a86e18/tumblr_mnn68qT24G1rx3l95o1_500.gif)