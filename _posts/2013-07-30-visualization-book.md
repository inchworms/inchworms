---
title: Visualize now - a book review (the first 60 pages!)
layout: post
created_at: Tue Jul 30 2013 22:00
permalink: /blog/2013-07-01-visualize-now
author: inchworms
twitter: inchworms_

---

Reading the book ["Interactive Data Visualization"](http://chimera.labs.oreilly.com/books/1230000000345) is not only very informative but also a lot of fun!

The first chapters cover a lot about Web-Technology, nicely and easy to follow explained. For expample how the web works:

* CLIENT: I’d really like to know what’s going on over at somewebsite.com. I better call over
there to get the latest info. [Silent sound of Internet connection being established.]
* SERVER: Hello, unknown web client! I am the server hosting somewebsite.com. What
page would you like?
* CLIENT: This morning, I am interested in the page at somewebsite.com/news/.
* SERVER: Of course, one moment.
15Code is transmitted from SERVER to CLIENT.
* CLIENT: I have received it. Thank you!
* SERVER: You’re welcome! Would love to stay on the line and chat, but I have other
requests to process. Bye!

See, thats what I mean. Or the useful Information that the inventor of the web, Tim Berners-Lee, regrets the two slashes in http://. [Source](http://bits.blogs.nytimes.com/2009/10/12/the-webs-inventor-regrets-one-small-thing/?_r=1)

**And here comes the informative part (bit abstract stuff):**

D3 is the Javascript library for creating Interactive Data Visualization. D3 means Data Driven Document. The Data is provided by YOU, the Document is anything that can be rendered by a browser and Driven is the connection between those two. It loads data to the browsers memory, binds that data to elements within the document or creates new elements, transforms those elements by interpreting each element’s bound datum and setting its visual properties accordingly and transitioning elements between states in response to user input.

**Get started (the fun part!!!!):**

To start with D3 first we have to download the javascript library [here](d3js.org/d3.v3.zip),decompress the zip file and move that folder in your project-folder. Now you create a empty index.html file and type that content: 

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <title>D3 Page Template</title>
        <script type="text/javascript" src="d3/d3.v3.js"></script>
      </head>
      <body>
        <script type="text/javascript"></script>
      </body>
    </html>

Your folder structure now should look something like this:

    project/
      d3/
        d3.v3.js
      index.html

The last thing to do is to set up a local webserver with phyton. Via the command line, navigate into the directory of the project and type:

    $ python -m SimpleHTTPServer 8888 &.

Vóila, its working. Type localhost:8888 in your browser and you will see - nothing. Nothing inside javscript, Dummy! To start with the first visualization, add inside the script tag in the body:

    var languages = ["English", "German", "Ruby", "Javascript"]

    d3.select("body").selectAll("p").data(languages).enter().append("p").text(function(n){return n;});

Now check if the webserver is still on, open your webbrowser and type: localhost:8888 and you will see the langages!


My favorite quote until now:

*"Linux users are born knowing how to open a terminal window, so I won’t waste your time explaining it here."*

:)



