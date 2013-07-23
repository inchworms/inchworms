---
title: Splatting and Slurping
layout: post
created_at: Tue Jul 23 2013 17:57
permalink: /blog/2013-07-23-splatting
author: inchworms
twitter: inchworms_

---

As [Don Jones](http://technet.microsoft.com/en-us/magazine/gg675931.aspx) points out, where else but the IT industry would one use a word like "splatting" in a serious, professional context? Or "slurping" for that matter. [osgx](http://stackoverflow.com/users/196561/osgx) explains it like this:

		In Ruby... [a] parameter of a method may be preceded 
		by an asterisk(*), which is sometimes called the 'splat' 
		operator. This indicates that more parameters may be passed 
		to the function. Those parameters are collected up and an 
		array is created.

		The asterisk operator may also precede an Array argument in 
		a method call. In this case the Array will be expanded and 
		the values passed in as if they were separated by commas.

Here's an example of what splatting can do:
		
		def drink(slurp, *flavour)
		  flavour.each { |f| puts "#{f}: #{slurp}" }
		end
		 
		drink("Slurping!", "Chocolate", "Vanilla", "Strawberry")

Will return:

		Chocolate: Slurping!
		Vanilla: Slurping!
		Strawberry: Slurping!

(See [Jaco Pretorius](http://www.jacopretorius.net/2012/01/splat-operator-in-ruby.html) for more examples)

The most common usage of the splat operator is, according to Jaco, slurping up all remaining arguments. But we were splatting Sinatra routes (or at least testing Sinatra's ability to support splat params). Mmmmm. Juicy.

<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=http%3A%2F%2Fapi.soundcloud.com%2Ftracks%2F102248467&amp;color=ff6600&amp;auto_play=false&amp;show_artwork=false"></iframe>
<p></p>

In any case, we're churning through our tests and learning way more about routes, and what web frameworks need to accomodate in URLs, than we ever anticipated. Konstantin made a nice [checklist](https://github.com/inchworms/sinatra_tests/issues/3) for us. We are happily ticking off the boxes :-)



