---
author: mdenomy
date: 2011-01-15 16:17:25+00:00
draft: false
title: Introduction to Test Driven Development at Nashua Scrum Club
type: post
url: /2011/01/15/introduction-to-test-driven-development-at-nashua-scrum-club/
tags:
- Agile
- Extreme Programming (XP)
- TDD
---

I had the opportunity to give a talk ["Introduction to Test-Driven Development"](http://www.meetup.com/nhscrumclub/calendar/15798972/) at the [Nashua Scrum Club](http://www.meetup.com/nhscrumclub/) this week.  It is a great group of folks, and if you are interested in learning more about Scrum and Agile practices you should check them out.  They are a diverse, engaging group of folks covering the full spectrum of roles in a Scrum organization.

The talk was targeted for all the roles on a Scrum team, and my goal was to give a small taste of what TDD can bring to a software project.  I have been using TDD for about 5-6 years, and I have definitely become ["test infected"](http://junit.sourceforge.net/doc/testinfected/testing.htm).  I can't imagine developing production code any other way.

I wanted to stress the importance of working iteratively, and getting through the [Red-Green-Refactor](http://jamesshore.com/Blog/Red-Green-Refactor.html) loop quickly, adding more and more functionality with each new test.  One of the areas new teams may struggle with TDD is to try and do too much in a single pass through the loop.  If you get bogged down and are in the loop for more than 15-30 minutes you may be biting off too much in this test and should look to a smaller incremental step.

Given the broad spectrum of roles that were at the meeting (Scrum Masters, coaches, QA/test, developers, managers, product owners) I also wanted to show how tests can be used to get the team to collaborate more.  I think tests can be a great mechanism for developers to collaborate with product owners to make sure the behavior is as intended.  There are also opportunities for QA/test to work with developers to understand what is tested at the unit and integration level.  Finally tests are a great mechanism for developers to share knowledge.  When I am looking at a code that I may not be as familiar with, I find the tests to be a great place to start to understand what functionality is provided.  In essence, the tests become an [executable specification](http://www.agilemodeling.com/essays/executableSpecifications.htm) of the system.

We also spent some time talking about TDD and design, which I know has been something of a hot-button topic [lately](http://blog.ploeh.dk/2010/12/22/TheTDDApostate.aspx).  Does TDD guarantee a good design?  Is it a good design methodology?  In and of itself, I would say no.  But what I would say is that TDD encourages good design practices and to do it well, i.e. not have brittle tests, you need good design practices.  I had almost 20 years experience before starting TDD and felt I was a good object-oriented designer.  TDD helped me step up my game in terms of design and developing more modular, loosely-coupled code.  We touched on design practices like [SOLID](http://en.wikipedia.org/wiki/Solid_%28object-oriented_design%29), [YAGNI](http://c2.com/xp/YouArentGonnaNeedIt.html), [DRY](http://c2.com/cgi/wiki?DontRepeatYourself), [separation of concerns](http://c2.com/cgi/wiki?SeparationOfConcerns), how design patterns like [MVC ](http://msdn.microsoft.com/en-us/library/ff649643.aspx)allow better, more thorough testing.

Finally we talked about the challenges of adopting TDD.  Change is hard, and a switch to TDD can be a difficult and frustrating experience.  TDD requires strong design practices.  There is also the battle to fight about writing "all that test code", to which I always like to ask "How much were you writing before".  Jim Shore summed it up well when he said that you should expect [2-3 months](http://jamesshore.com/Agile-Book/test_driven_development.html) to make the adjustment.

I had a great time at the Nashua Scrum Club, and want to thank everyone there for making it a fun (and hopefully informative) evening.  I look forward to a return visit soon.

<iframe src="//www.slideshare.net/slideshow/embed_code/key/zHGNJP3GEX34pe" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/mdenomy/introduction-to-test-driven-development" title="Introduction to Test Driven Development" target="_blank">Introduction to Test Driven Development</a> </strong> from <strong><a href="https://www.slideshare.net/mdenomy" target="_blank">Michael Denomy</a></strong> </div>
