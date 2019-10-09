---
author: mdenomy
date: 2008-10-25 12:19:51+00:00
draft: false
title: Getting Started with Rally
type: post
url: /2008/10/25/getting-started-with-rally/
tags:
- Agile
- Rally
---

I have been using Agile techniques on a regular basis for about 3 years now.  The team I work in has gone through some interesting evolutions with our iteration and release planning, and at the moment we are using Rally as our planning tool.

A little history first might be helpful in how we got here.  Early in the project it was just 2-3 developers and we were all developing C# code, using Visual Studio Team System.  Team System has a pretty good work item and defect tracking system.  You can enter defects, tasks, provide time estimates, and have dependencies between tasks.  Another really nice feature was that your check-ins could be linked to a task/defect, so to go back and see what changes were made in the code against the work item was pretty easy to do.

When the team was smaller this approach worked pretty well.  Our iteration planning meeting involved going through the open defects and work items (tasks, essentially).  Most of what had to be done was implicitly understood by the stakeholders, so priorities were typically pretty clear and mostly it came down to a scheduling exercise.  Team System did not seem to have any good mechanism for defining user stories and linking them to tasks, but with a smaller group of stakeholders and developers we were able to get by without a lot of user stories.  Was it a mistake to not put more effort into user stories?  Maybe, but that was the world we lived in.

All this worked pretty well while the team was small, but as the team grew it became more unwieldy.  There was no mechanism to graphically display the tasks and do any long term planning.  It was just a big task list.  You could sort it, but being able to lay it out graphically was not supported.  For a time we used a manual process where major tasks were put into a Visio diagram and grouped into iterations.  That allowed the team to see how functionality would be rolled out, but keeping it in sync with the work item system was a manual process and difficult and time consuming at best.  There was also no automated way to see if we were overloaded.

As the size of the team grew both in terms of developers and other stakeholders, we needed to find another solution.  We looked at several tools and decided to try out [Rally](http://www.rallydev.com/).  Rally’s Community edition is free for up to 10 developers.  It also has some of the features that I found were missing in our previous process.



	  * Graphical- Easy to drag and drop stories into different iterations and see when new  functionality will come online
	  * Supports resource loading, so we can see how our iteration and release plans measure up against available resources
	  * Hierarchical – Everything starts with a user story or a defect.  Tasks are grouped under the user story or defect.  It is also possible to have a hierarchy of user stories to group and plan related functionality.
	  * Supports releases and iterations, so I can plan when formal releases will be available and easily see what feature sets (user stories and defects) will be in them.
	  * Built in reporting tools for defects, and iteration burn down rate.

Like any tool it has a few warts, and I am sure I will get around to posting about them.  But in the two months I have been using it I am pretty pleased.
