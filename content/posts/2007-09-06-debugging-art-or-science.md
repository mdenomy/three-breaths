---
author: mdenomy
date: 2007-09-06 04:00:46+00:00
draft: false
title: Debugging - Art or Science?
url: /2007/09/06/debugging-art-or-science/
tags:
- Debugging
- Software
---

I write a lot of instrumentation and laboratory automation software, and I invariably utilize 3rd party software and hardware. Talking to the  vendors these products work perfectly every time, and in most cases they do, but invariably things go wrong. So an important part of my job is diagnosing and debugging hairy integration problems. Automation applications typically utilize multiple threads and processes and that adds to the complexity of  the debugging effort.

I've heard people describe debugging as more of an art than a science.  For grins, I googled "Art of Debugging" and I got 16,700 hits.  There is certainly a lot of skill and hard work that goes into debugging, but I'm not so sure it qualifies as an art.  To me, good debugging is the result of up front planning, careful observation, intuition, experience, and probably a bit of luck.

### Instrument Your Software

Debugging without the benefit of trace or log data is going to make your life difficult.  Log files are really helpful for me when it comes to recreating the sequence of events leading up to a bug.  A couple of tools I find really helpful are [log4net](http://logging.apache.org/log4net/) and [BareTail](http://www.baremetalsoft.com/baretail/).

Log4net is a logging framework that allows you to write log output to a variety of sources: rolling disk files, database, Telnet, UDP, and many more.  Changing how data is output is done by configuration file and you are able to filter and control output in a variety of ways.  There are a lot of good examples on the log4net site and elsewhere on the web  and this is a tool you should really look into if you are developing in .NET.  The Java folks already know this as log4net is a port of log4j.  Thanks again Java folks for paving the way for us .NET developers.

BareTail is a tail utility for windows that has some nice features like highlighting and allows me to watch log files dynamically. Give it a try if you find yourself in a situation where watching log files “live” is important.  There is also a companion tool called BareGrep that you may have guessed is a grep utility.

When you write code, you should try and be sure you are adding the capability to record significant events. It’s never too late to start adding logging.  If it’s not in there, or there’s not enough, add some.  If an intermittent bug crops that leaves you stumped, put in some additional logging and maybe next time the bug occurs you’ll have more to go on, or at least something to eliminate.


### Experience and Intuition

These are the kind of intangible skills that might push debugging into the "art" category for some people.  Experience and intuition are really helpful in terms of narrowing the possible causes of the problem and how to identify it.  This is especially true if you are picking up some legacy code and don't have a full understanding of all the inner workings of the code.   Good debuggers have a knack for zeroing in on a particular part of the code and getting to the root of the problem.

I got assigned a bug recently where it appeared that we were processing the same record twice.  This was also a piece of code that I had not worked in much.  There were several processing threads and the likely culprit was that the queuing/dequeuing of records was not thread-safe.  A quick look through the code showed this not to be the case, so I was a bit stumped.  What else could the problem be?  The error message indicated that a record with a particular ID was being processed twice.   Then it hit me, how is the ID assigned.  It turned out that when the records were constructed there was a pre-increment of the ID that was not thread-safe.  This code had been running for months without the error occurring but eventually those once in a million bugs crop up.  This is an example of where intuition saved me from what could have been a long exercise of going through the code line by line or the dreaded "unable to reproduce".


### Pay Attention to The Data

Intuition can really help narrow the scope of your efforts, but I have also seen this work against people when they went into the debugging task with a particular idea in mind and ignored or missed signals that would have pointed them in a different direction.  They were too focused on what they thought "must be the problem".

I recently worked on a camera system that was getting spurious triggers.  Electrical noise problems are notoriously difficult to find and this had all the marks of a noise problem.  I'm not an electrical engineer, but the hardware guys on the team had some possible suspects that they wanted to investigate.  The thinking was that something else in the system was creating intermittent noise on the camera trigger lines.  I was going to set up a test that would exercise various parts of the system and monitored the camera logs for unexpected images being triggered to try an identify what components were causing the noise.


Just before the test was ready to be run I wanted to verify that the log would record unexpected images, so I manually triggered some images by driving the trigger signal with a UI test application that came with the IO device.  I expected to see one image when I enabled the trigger but then I saw a second image when I turned off the trigger.  At first I though maybe I double-clicked instead of clicked so I tried it a few more times. Usually I only got the expected single image, but every once in a while I got two images.  What we thought was going to be a difficult problem to reproduce was now fairly easy to reproduce.  I got lucky on this one because the triggering issue was exacerbated by the difference in timing between an automatically triggered image (tens of milliseconds) versus the manual triggered image (hundreds of milliseconds).  But if I wasn't paying attention to the logs ([log4net](http://logging.apache.org/log4net/) and [BareTail](http://www.baremetalsoft.com/baretail/) again) or waved it off as operator error I would have missed a valuable clue.

### Art or Science
Debugging is about preparation and hard work, being guided by your instincts, but also knowing when you are looking in the wrong place and coming up with another plan.
