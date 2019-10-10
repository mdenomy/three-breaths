---
author: mdenomy
date: 2012-06-14 13:06:22+00:00
draft: false
title: Stone Soup Development
url: /2012/06/14/stone-soup-development/
tags:
- Agile
- Retrospectives
- TDD
- XP
---

I consider myself lucky to work in an environment that not only follows, but embraces, Agile and XP practices.  We follow [test-driven development](http://mdenomy.wordpress.com/category/tdd/).  We [pair program](http://mdenomy.wordpress.com/category/pair-programming/) almost all the time, and we switch pairs frequently, usually at least once per day.  The benefits of these practices hit home this week during our iteration [retrospective](http://mdenomy.wordpress.com/category/retrospectives/) when the question was posed “What were you proud of this week”.

There were some interesting problems with very creative solutions that happened during the iteration, but the thing I was most proud of was a simple little piece of code.

Around the middle of the iteration I worked on a “calculator” that made some determination based on a set of rules.  We've all written code like this 1000 times before, it was not an especially difficult task.  But it was the kind of thing that could get ugly pretty quickly, and yet still “work”.  It was the kind of algorithm that could have easily morphed into a nasty tangle of boolean logic.

Instead, my pair and I started out with a few simple cases and applied a few brute force implementations in the “Calculate” method.  We [continuously refactored](http://jamesshore.com/Agile-Book/refactoring.html) as more tests were added and the complexity grew, reducing duplication and breaking the problem up into more digestible chunks.  At some point, my original pair swapped out and someone else swapped in for an hour.  It was late Friday, we improved some of the naming, added a few more test cases and supporting logic, then called it a day.  [Energized work](http://jamesshore.com/Agile-Book/energized_work.html) in action.

Monday morning, a new person swapped in.  Normally I would have swapped out since I had been on it the longest, but there were a few scheduling conflicts and so I stayed on.  We finished the class, ending up with very expressive names, a “Calculate” method that read like plain English, and small methods that did one thing, and did them right.  Again, this problem wasn't rocket science, but it was done right.

Everyone brought something to the problem and helped refine the design.  We discussed trade-offs, avoiding traps like “my idea” and “your idea”.  After discussing it at the retrospective, it reminded me of a story that I learned as a kid called [Stone Soup](http://en.wikipedia.org/wiki/Stone_soup#Story).  We started with nothing, everyone threw a little something in the pot, and we came out in the end with a nice little piece of code.
