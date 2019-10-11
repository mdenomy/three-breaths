---
author: mdenomy
date: 2012-07-20 12:29:23+00:00
draft: false
title: Craftsmanship and When Not To Refactor
url: /2012/07/20/craftsmanship-and-when-not-to-refactor/
tags:
- Software Craftsmanship
---

I love learning how to write better software.  That was the attraction for me to the [Software Craftsmanship](http://manifesto.softwarecraftsmanship.org/) movement.  Here is a group of folks that are concerned about developing  software in a way that is extensible, testable, and maintainable.  I have learned so much about techniques like [SOLID](http://en.wikipedia.org/wiki/SOLID_(object-oriented_design)), different [pair-programming](http://mdenomy.wordpress.com/category/pair-programming/) strategies, TDD, DRY, and the list goes on and on and on.

But let's not lose sight of our jobs here.  We are paid to develop **features** that our customers **need**.  Our customers are not going to care how the software is crafted under the covers, unless it gets in the way of us being able to add new features, extend existing ones, or provide a reliable platform.

We have an awesome team room where I am working, with all kinds of [information radiators](http://alistair.cockburn.us/Information+radiator) that help us do our jobs and communicate to our customers how we are doing.  We keep our retrospective goals on 3x5 cards in a visible place so they stay fresh in our minds.  Lately, as a result of some pain we felt adding new features, we have been pushing hard to refactor code that gets in our way or makes it difficult to extend the software.

Here are what two of the cards remind us about our refactoring practices:

<blockquote>Refactor all the time as you go.</blockquote>


This encourages us to keep the code clean while we are developing in, remembering the "refactor" in the "[red-green-refactor](http://jamesshore.com/Blog/Red-Green-Refactor.html)" loop and avoiding the "red-green-red-green-red-green-refactor-refactor-refactor-refactor-refactor-refactor" anti-practice.

<blockquote>If any code is slowing you down, change it (in small slices)</blockquote>

This drives us to fix code that is making it difficult to maintain or extend the code.

There is no card though that says _"If you see something you don't like, change it"_, and I think this is where you can get in trouble with the notion of "[merciless refactoring](http://c2.com/xp/RefactorMercilessly.html)".

We've all written code we don't like or would write differently knowing what we know now as opposed to last year, last month, or even last week.  But that is not carte blanche to re-write something just because it comes into our eye-line.  If it gets in our way, that's a different story, but we need to keep our eyes on the prize and that prize is the new feature that we promised our customer at the end of the iteration.

Anyway, that's my two cents.  This [soap-box](http://en.wikipedia.org/wiki/Soapbox) I am standing on is starting to creak, so I better get down now.  Please feel free to share your thoughts or observations.

P.S. In thinking about this I saw some good posts on the subject that you may find interesting:

[http://devblog.avdi.org/2012/06/25/every-day-in-every-way/](http://devblog.avdi.org/2012/06/25/every-day-in-every-way/)

[http://dannorth.net/2011/01/11/programming-is-not-a-craft/](http://dannorth.net/2011/01/11/programming-is-not-a-craft/)
