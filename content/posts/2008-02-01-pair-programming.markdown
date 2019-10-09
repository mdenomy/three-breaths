---
author: mdenomy
date: 2008-02-01 02:54:12+00:00
draft: false
title: Pair Programming
type: post
url: /2008/02/01/pair-programming/
tags:
- Agile
- MbUnit
- NUnint
- pair programming
---

I've been doing some pair programming this week and have found the experience to be extremely productive and informative.  I am pairing with a guy named Mike, who is someone I have worked with in the past and really enjoying working with.    We are in the midst of a fairly significant refactoring effort for a particular component.

Although Mike and I often bounce ideas off each other when we are working individually, I think the quality and flow of ideas is significantly better now that we are pairing.  That only makes sense I guess.  Even if it is code that you are familiar with, when someone asks you a question while you are working on something else it is difficult to grasp the subtleties of the problem.  During this pairing effort we are both intimately familiar with the underlying problems and can quickly comment on strengths and weaknesses of a particular approach.  The design is really coming along well and we have been able to address issues regarding complexity, [IOC](http://martinfowler.com/articles/injection.html), and enhanced testing.

Speaking of testing, this component has a good suite of tests and that is a real blessing when you are refactoring.  I feel a lot more confident after a significant change to see "All tests passed".  I have been using [NUnit](http://www.nunit.org/index.php)/[MbUnit ](http://www.mbunit.com/)for about 3 years now and I am trying to remember what programming was like before I had these tools.  We are trying to work incrementally and each time we get to a stable point we are checking in the changes.

I have to admit that at times pair programming was tough to get used to.  On the first day I found myself saying things like "if you want to go work on XYZ I can run with this for a bit and we can get back together later".  Usually this would happen when we hit a snag and I needed time to think though the problem.  I was uncomfortable _**not **_writing code in front of someone else, even though when I am working alone I recognize this non-coding time as part of moving forward.  Something about not having an immediate answer in front of someone else made me feel very uncomfortable.

There have been a lot of positives to the effort, and so far no negatives.  I am sure that some of that is due to that fact that Mike and I work well together and have similar beliefs about software development.  That is not to say we have always been in agreement, and indeed have had some spirited discussions.  We have come up with a design that is stronger than either of us would have come up with individually.  We are pushing each other to develop and maintain good tests, and also to push back with the occasional [YAGNI ](http://simonwillison.net/2003/Dec/9/yagniAndDry/)criticism.  We are also sharing productivity tips, comments about programming styles, ideas about new tools, blog posts, etc, etc.

One unexpected benefit of this pair programming effort has been that people have been less willing to interrupt us when we are working together.  Maybe it is seeing two people working productively and enthusiastically that makes people hesitate before interrupting.  There have been interruptions but they are fewer and we have also been more willing to say "let me finish up what we are doing here and I can swing by in 30 minutes".

I am really looking forward to doing more of this.  Based on the quality of the code and tests and our overall productivity I would feel confident defending the use of two developers for one task to management.  I would also like to try pairing up with other members of the team.  I am sure we will go through some of the same awkward startup moments but I think there is a lot to be learned and shared.
