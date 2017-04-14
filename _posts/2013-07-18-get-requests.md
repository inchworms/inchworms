---
title: Getting Get Requests
layout: post
created_at: Thu Jul 18 2013 14:30
permalink: /2013-07-18-get-requests
author: inchworms
twitter: inchworms_

---

First of all, [Cecilia](https://twitter.com/_ceciliarivero) from #rgsoc-teams, we hope you're feeling more yourself.

![cecilia](/inchworms/images/cecilia.png)

Secondly, when trying to communicate (to someone remotely) what you're actually inputing into your terminal, it's possible to make a video capture of your screen online and send a link to your remote buddy. Just use [ascii.io](http://ascii.io). 

We weren't able to access our localhost server using telnet so sent this to Konstantin:

<script type="text/javascript" src="http://ascii.io/a/4235.js" id="asciicast-4235" async></script>
<p></p>

Our mistake was failing to simply enter an empty line...

Why were we doing this? Because yesterday we started writing tests for Sinatra, focusing initially on all the HTTP requests. Using telnet is one way of seeing what the server response is. Useful for us to see what we would be testing for.

Actually Konstantin hand drew some requests/responses for us yesterday.

We also did a bit of reading at lunch from [Sinatra: Up and Running](http://shop.oreilly.com/product/0636920019664.do). It has a nice little [example app](https://github.com/inchworms/rock_paper_scissors) in Chapter 1 that lets you play Rock Paper Scissors with your computer. It's super simple, but very instructive!
<p></p>

![books for lunch](/inchworms/images/booklunch.jpg)

AND we wrote a few tests: GET returns 200 as a status, returns body as string, returns body as array; GET /hello returns the exected route.

More tomorrow.

