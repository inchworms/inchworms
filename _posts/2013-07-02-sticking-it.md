---
title: Sticking Things to the Wall
layout: post
created_at: Tue Jul 02 2013 18:50
permalink: /blog/2013-07-01-sticking-it
author: inchworms
twitter: inchworms_

---

We continued working on our sample app [Songs By Nancy](https://github.com/inchworms/songs_by_nancy). 

Before implementing a database, and with it the ability to add and remove content, we worked with a static file of data first (as per Matt's suggestion). This involved creating a spreadsheet file, exporting it as a csv file, converting this file to JSON, then parsing the JSON file into a ruby hash. All in a morning's work ;-) 

(Actually, Anja was pretty excited about learning how to do this and Carla was amazed that she remembered - from hack-day projects she'd worked on - how it could be done).

Then there was a bit more faffing about with a couple of new pages (one to display a list of songs, one to display individual song lyrics), which meant new templates, and some changes to the main.rb.

Our next task was to sketch up an outline of what the structure of our tutorial would look like. We charted several steps, which we divided into parts. Each part will form the basis of a screencast:

		Building a Basic Website - Screencast Outline

		Part 1 - Basic Requests, Defining Variables, Using Sinatra Reloader
		Part 2 - Views, Layouts, Partials, Folder Structure, Images, CSS
		Part 3 - Using Static Data, Creating a Database, Adding/Editing/Deleting Content
		Part 4 - Error Handling

Konstantin, meanwhile, refused, despite our insistence, to print the single-page literary epic that is Sinatra's base.rb. We wanted to stick it to the wall and draw flow-arrows between which parts of the file interacted with other parts of the file. Herr Haase, however, was dubious. 

22 pages? A ridiculous idea! 

Were we deterred? No! 

We hopped onto the [Ezeep](http://ezeep.com) printing service, found a printer on Level 3 of the same building, and within miniutes had the 22 page document plastered to the wall. 

Unsurprisingly it took less than another half minute for Konstantin to appear and admire his handiwork. Where he remained for the rest of the afternoon.

<iframe width="360" height="640" src="//www.youtube.com/embed/Sc15a4wZLfQ?rel=0" frameborder="0" allowfullscreen></iframe>
<br>
Tomorrow rkh promises to print out [Almost Sinatra](https://raw.github.com/rkh/almost-sinatra/master/almost_sinatra.rb). It should take up a little less space...

