---
title: Sequel Models
layout: post
created_at: Wed Sep 04 2013 17:11
permalink: /2013-09-04-sequel-models
author: inchworms
twitter: inchworms_
---

Today we created model classes for each of our database tables. It was way easier than we expected and required just a single line: **class Year < Sequel::Model; end**. Sometimes reading the documentation yields quicker-than-expected results!!

Then, after adding associations between the classes (such as **one-to-many :recipients**) we were able to dig around our dataset objects and look at (for example) what methods were available to what objects. **payments_sorted.all.first.values.methods** returned a different list of available methods to **payments_sorted.all.methods**.

We also worked out how to see what columns an object contained, and how to add a new key/value combination to it. 

Tomorrow we're both installing SSDs into our laptops. This *may* mean our computers will be out-of-action at the end of the day, so we may not be able to post here tomorrow...

![ssd](/inchworms/images/ssd.jpg)

