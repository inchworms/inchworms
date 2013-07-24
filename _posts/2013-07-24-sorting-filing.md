---
title: Sorting and Filing
layout: post
created_at: Wed Jul 24 2013 17:10
permalink: /blog/2013-07-23-sorting-filing
author: inchworms
twitter: inchworms_

---

Our routing_spec.rb document was getting rather long and confusing. Scrolling up and down it hurt our brains, not to mention had us inserting new tests into wrong contexts. 

So we broke the file up into a bunch of seperate files based on contexts. Now our directory structure looks something like this:

![spec directory structure](/images/directoryStructure.png)

You'll notice a folder called 'unchecked'. This hold the files we've already written tests for but need to check (Matt discovered this morning that some of our test, whist passing, are not actually testing for what they should be).

You'll also notice some other folders for other types of requests, like put, post, link, etc. We have to finish the get requests first!

We also learnt that if you list tests without implementing them,  like this...

![test list](/images/testlist.png)

... when you run the test, the output will look like this:

![pending](/images/pending.png)

That is, the unwritten tests will be listed as "PENDING: Not yet implemented." Neat, huh!

Meanwhile, our commits for the day (as of 5pm) look like this:

![Commits July 24](/images/comitsJuly24.png)