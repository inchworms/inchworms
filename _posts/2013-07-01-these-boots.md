---
title: These Boots Were Made for Walkin'
layout: post
created_at: Mon Jul 01 2013 19:00
permalink: /blog/2013-07-01-these-boots
author: inchworms
twitter: inchworms_
---

We spent a couple of hours in the morning with Matt having CGI (Common Interface Gateway) explained to us. It's the old-school way of doing simple dynamic content on the web.

He then walked us through FastCGI, SimpleCGI, and WSGI until he arrived at Rack, the current protocol that Rails and Sinatra apps use for passing requests and responses back and forth across the internets. [This post](http://www.amberbit.com/blog/introduction-to-rack-middleware) by Hubert Łępicki was very useful in explaining how Rack works.

We were then set the task of building a simple Sinatra app. We used a tutorial from the excellent ["Jump Start Sinatra"](http://www.sitepoint.com/books/sinatra1/?utm_source=sitepoint&utm_medium=email-newsletter&utm_campaign=sinatra1) book by Darren Jones. We modified his sample app a little. You can check out our initial work [here](https://github.com/inchworms/songs_by_nancy). We've still got more work to do but we've learnt some fundamentals about how Sinatra works.

We also had to make a diagram of the basic way a Sinatra app handles a request. We came up with this, a messy representation of how an app talks to a client:

![rack Diagram](/images/rackDiagram.jpg)

On the http level this is what Sinatra is doing:

![http Diagram](/images/httpdiagram.jpg)

more or less...

