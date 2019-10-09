---
author: mdenomy
date: 2015-01-08 03:13:39+00:00
draft: false
title: Getting Started with Haskell - Comprehending List Comprehensions
type: post
url: /2015/01/07/getting-started-with-haskell-comprehending-list-comprehensions/
tags:
- Haskell
- Season of Haskell
---

[As promised](http://mdenomy.wordpress.com/2014/12/31/its-time-to-go-functional/), we are now in the Season of Haskell.  I decided to spend this week with some baby steps and also try to figure out what resources to use to get started.  I had heard good things about [Learn You a Haskell For Great Good](http://learnyouahaskell.com/) and [Real World Haskell](http://book.realworldhaskell.org/).  I felt like reading the first few chapters of each would give me a feel for the book styles and let me narrow my focus.

I have to say that there are certainly some neat things that Haskell can do in a fairly terse syntax. List comprehensions are pretty cool. There is an [example](http://learnyouahaskell.com/starting-out#tuples) in Learn You a Haskell that allows you to find all the right triangles with a hypotenuse less than 10 in one (fairly) simple line, once you start to grok the syntax.

[code lang=text]
[ (a,b,c) | c <- [1..10], b <- [1..c], a <- [1..b], a^2 + b^2 == c^2] 
[/code]

What this says is get me the list of points, actually tuples, (a,b,c) where




  * c is drawn from the range 1..10
  * b is drawn from a range of 1..c
  * a is drawn from a range of 1..b
  * and the predicate function a^2 + b^2 == c^2 is applied to test that it is a right triangle


The result is [(3,4,5),(6,8,10)]

Versus something like this in Ruby

[code lang=ruby]
rightTriangles = []
(1..10).each do |c|
  (1..c).each do |b|
    (1..b).each do |a|
      if (a**2 + b**2 == c**2)
        rightTriangles << [a,b,c]
      end
    end
  end
end
[/code]

Obviously Ruby has a lot of other strengths going for it, but clearly this is the type of problem where functional languages may shine.  And who knows, there may be ways to bring some of these ideas into my Ruby programming.  Might be a good time to re-watch [Pat Shaughnessy's talk on Functional Programming and Ruby](http://www.confreaks.com/videos/2557-goruco2013-functional-programming-and-ruby).

I'm curious to see what comes next.
