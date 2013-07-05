---
title: Validation Sux
layout: post
created_at: Fri Jul 05 2013 17:06
permalink: /blog/2013-07-05-validation-suxxxxxx
author: inchworms
twitter: inchworms_

---

It really does.

We got most of our form fields validating but couldn't work out how to handle the date field.

We did discover that some browsers (eg Chrome) automatically display a funky calender selector input thingy if the html form input type is set to "date":

		<input type="date" name="song[released_on]">

Which looks a little funky, if you ask us:

![date entry field](http://i.stack.imgur.com/5Pzjv.png)

So since Firefox ignored "date" as an input type, meaning we'd need to reformat whatever was entered with a Firefox browser into something our app would recognise as a date, we decided to make the input type "text". Less code to write and more uniformity across browsers...

But we still had trouble working out how to code things in a way that would force the user to enter data in the format we needed (dd/mm/yyyy). After several failed attempts we decided we need detailed coaching help, so while we waited for that we went back to version 1 of the app, which we tidied up and deployed to Heroku. You can now visit a working version online [here](http://songs-by-nancy.herokuapp.com).

Next week we'll start recording screencasts to guide viewers through all the steps we took to build the different versions of our apps. Our plan at the moment is to put the relevant code for each step into a seperate github branch - but Carla's thinking it might be better to simply make a seperate section in our inchworms blog gh-pages for any tutorials we create and embed the code there. We'll work all this out on Monday.

So, we're almost at the end of week one, and we're more-or-less on track. Matt's due any second to help us crack our date validation conundrum, so hopefully we'll solve that before today's close of play. 

Have a happy weekend y'all :-)








