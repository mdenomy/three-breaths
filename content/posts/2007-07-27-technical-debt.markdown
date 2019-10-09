---
author: mdenomy
date: 2007-07-27 13:41:47+00:00
draft: false
title: Technical Debt
type: post
url: /2007/07/27/technical-debt/
tags:
- Agile
---




I first heard the term technical debt in reference to a post by [James Shore](http://www.jamesshore.com/Articles/Business/Software%20Profitability%20Newsletter/Design%20Debt.html) (which he credits to Ward Cunningham).  I once worked on a system that had a component that the development group referred to as the [cloaca](http://en.wikipedia.org/wiki/Cloaca), which is Latin for sewer.  It was poorly designed and included a lot of “features” that “might” have been needed down the line.  It also suffered from a dearth of good unit tests.  It worked, but it was difficult to maintain.




In my book this goes against the whole idea of Agile and iterative development.  Adding functionality that you “think” might be needed, without any direction from stakeholders is typically not a good idea.  It tends to muddy up the code and if the functionality is eventually needed it is unlikely that your initial implementation, designed without stakeholder input, is going to satisfy the desired functionality.  That is not to say that we should not think of extensibility when we design or not to challenge stakeholders for more/less functionality.  However, you shouldn’t be designing in a vacuum or adding features because you alone think they should be there.




Every iteration I heard of tasks taking longer than they should have because we were getting mired in this component.  What should have been a simple change often turned out to be harder to implement than expected and often had unforeseen consequences.  The unfortunate ones who picked up this code tried to add some unit testing, but it is always harder to add tests after the fact than to start with testing in mind.




Earlier in the project we had talked about fixing this component, but schedule pressure got the better of us.  We paid the price down the line, each and every iteration, in terms of developer hours and system reliability.  And each time we added functionality that tied into this component we knew it would become harder and harder to fix.




Finally a decision was made to try and address some of the complexity and refactor this component.  It was not all done in one shot, just small incremental improvements over time, sometimes just an hour or two taken as a bit of a mental break from more rigorous tasks.  The lack of unit tests made refactoring more challenging because there were no good tests that defined the intended behavior of the component and no way to know that refactoring was not causing unforeseen consequences.   Writing a unit test was usually the first task in one of these refactoring sessions.




When you write code






  * Only put in the functionality that is required.
  * Don’t write code without writing tests
  * If the interest on technical debt gets too high, it’s time to pay down

