---
title: The Docs, The Back Trace
layout: post
created_at: Fri Jul 05 2013 17:53
permalink: /blog/2013-07-08-docs-back-trace
author: inchworms
twitter: inchworms_

---

Checking the documentation and looking at the error back trace was the theme of today. We though we'd sucessfully implementing the date validation on Friday afternoon, but we realised over the weekend that it was only working properly when we created a new song, not when we updated a song.

Matt left us in the morning with the task of working out how to fix this. His parting words were "Check the documentation and read the back trace".

We spent most of the morning doing the following:

<img src="http://www.kaputtmutterfischwerk.de/wp-content/uploads/2013/07/Falling-asleep-master-level.gif" alt="pillow kiss" style="width: 500px;"/>

The issue (we eventually realised, with Urs' help) was that we were checking validation not on the newly entered data but on original data in the song. We had to instead make sure we were checking the updated data. This meant changing 

		song = Song.get(param[:id])
		if song.valid?

to

		song = Song.get(param[:id])
		if song.update(params[:song])

It only took us 3 hours to work this out :/

We then tried to customise the error messages that DataMapper raised. And had some success doing this. But still couldn't manage to override the default error message on the date field validation. We might look at this again tomorrow.

We switched to preparing for the screencasts we plan to record for our https://github.com/inchworms/songs_by_nancy/tree/Tutorial-Part-2sample app tutorial, changing our outline a little:

    Building a Basic Website - Screencast Outline

    Part 1 - Installing Sinatra, Basic Requests, Routes, 
    		 Inline Views, Using Sinatra Reloader, Dynamic Variables
    Part 2 - Layouts, Folder Structure, External Views, 
    		 Partials, Instance Variables, Images, CSS
    Part 3 - Using Static Data, Deploying to Heroku
    Part 4 - Using a Database, Add/Edit/Deleting, Validations

We wrote rough scripts for Parts 1 & 2, and created branches in github where people will be able to download relevant files: [Part 1](https://github.com/inchworms/songs_by_nancy/tree/Tutorial-Part-1) and [Part 2](https://github.com/inchworms/songs_by_nancy/tree/Tutorial-Part-2)

![script](/images/script.jpg)

Tomorrow we'll start recording screencasts for these. 