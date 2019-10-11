---
author: mdenomy
date: 2007-11-02 13:39:27+00:00
draft: false
title: Credibility and Trust
url: /2007/11/02/credibility-and-trust/
tags:
- Continuous Integration
- Software
- Unit Testing
---

Software is one of those industries that can suffer from credibility issues.  We have all had painful experiences with buggy applications or operating systems that have been thrust upon us.  Software, like any product, will have failures.  Some failures will be more obvious or serious than others, some may only arise in unusual situations or in unforeseen conditions.  As good developers it is our job to limit these errors and avoid having serious ones get to the end user.  Automated test and continuous integration tools go a long way towards helping us accomplish those goals.

I've worked in environments where I was the only software developer (as well as QA, config management, and tech support all rolled into one).  Other places had full blown SQA, test department, etc.   In all of those environments I had a "customer".  Sometimes it was someone external to the company who paid money for the software we produced, other times it was an internal R&D user or the software test department, or maybe it was just a teacher in a class I was taking.  In all these cases, the "customer" is expecting a reliable piece of software to do the task at hand.  If you release a buggy piece of software, be it to a real paying customer, an internal R&D organization, or a professor you are going to have credibility issues that will be difficult to overcome.  Subsequent releases will be received with varying degrees of skepticism.

One of the first times I began using continuous integration and automated unit tests was at an R&D facility.  The customers were coworkers that you would see every day, and if things weren't going well you knew about it.  When I came on board as part of a new team of developers, the group was just beginning to employ CI and unit testing.   The previous group that developed software did various levels of ad hoc testing.  Often the tests were manual tests that involved examining log files or single stepping through critical sections of code.  Often times a fix would introduce new problems, and the end users suffered the consequences.  There was an understandable lack of trust between the users and the developers.

I remember early in the process telling end users that new releases were available, but they would choose not to upgrade.  It took a long time to build a framework that gave us good unit test coverage and procedures to perform system level testing in a meaningful way.  This organization did not have a software test or QA department so it was the developer's job to ensure that reliable software was being released.  That may not be an ideal situation, but I have worked in more organizations without a software test department than ones that had one.  Believe me, I wish we had one but we didn't.  Slowly as we increased automated test coverage we began to provide more reliable software and rebuild the trust that had been damaged by previous experience.  It was very rewarding when users would ask when new releases would be available.

Sometimes we are pressured to get changes out the door in a hurry and invariable there is a temptation to skimp on testing, but the damage that can be done by a bad release can have long lasting effects.  Trust and credibility are easily damaged and take a long time to restore.  As professional developers, it is our job to ensure that what we release has been tested and is reliable.  Sometimes that means balancing the demands to get things done fast with getting them done is a way that they are well tested and reliable.
