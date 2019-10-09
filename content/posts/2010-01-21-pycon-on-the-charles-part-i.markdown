---
author: mdenomy
date: 2010-01-21 16:47:25+00:00
draft: false
title: PyCon on the Charles - Part I
type: post
url: /2010/01/21/pycon-on-the-charles-part-i/
tags:
- mocks
- Python
- testing
- Unit Testing
---

I have been doing some work with Python the last few months and recently joined a [Python Meetup group in Cambridge](http://python.meetup.com/181/) that had a meeting last night at [Microsoft NERD](http://microsoftcambridge.com/Default.aspx).  The purpose of the meeting was a chance for some people who are presenting at [PyCon](http://us.pycon.org/2010/about/) to do a dry run on their presentations.  The meeting was called [PyCon on the Charles - Part I](http://python.meetup.com/181/calendar/12189514/) 


This meeting definitely met my [one good thing rule](http://mdenomy.wordpress.com/2009/12/10/one-good-thing/), in fact I thought all the presentations were interesting.  There were three presentations



	  * Python for Large Astronomical Data Reduction and Analysis Systems by Francesco Pierfederici
	  * Python's Dusty Corners by Jack Diederich
	  * Tests and Testability by Ned Batchelder 


Francesco Pierfederici talked about how he uses Python in "Big Astronomy", particularly for the [LSST ](http://www.lsst.org/lsst)project.  The code base they are using has a [pipeline framework](http://lsstdev.ncsa.uiuc.edu/trac/wiki/PipelineFramework) that I am interested in looking at.  There is a lot of simulation that needs to be done before building a large telescope and the supporting computing infrastructure.  Most of the high level code is developed in Python, with the computation intensive code written in C.

I was most interested in the [Ned Batchelder's](http://nedbatchelder.com/) Tests and Testability presentation because I am interested in the tool support for testing in Python.  He presented techniques to using mocking to make your code more testable, as well as ways to structure your code to support dependency injection.  The mocking framework was Michael Foord's [mock](http://www.voidspace.org.uk/python/mock/).  

I would have liked to have seen more emphasis on addressing testability early in the development cycle.  As a proponent of [TDD](http://en.wikipedia.org/wiki/Test-driven_development), I think you need to begin testing as soon as you start developing.  In my experience it leads to a better design through loose coupling and you avoid having to make a major refactoring to put in test hooks after the fact.  I think Ned did a nice job presenting the techniques and some of the tools available in Python to make testing easier and with better coverage.

All in all, an interesting evening and if you are a Python developer in the Boston/Cambridge developer you may want to join up.  There is a follow up on scheduled on 2/3/10 called [PyCon on the Charles - Part II](http://python.meetup.com/181/calendar/12189588/) where there will be three more practive presentations for PyCon.

And once again, kudos to Microsoft for making their space available for different groups.  This is the 4th event that I have been at in their space and exactly none of them were Microsoft specific.  I think having a space where developers can get together is something that has been sorely lacking and they deserve credit for trying to make that happen.

