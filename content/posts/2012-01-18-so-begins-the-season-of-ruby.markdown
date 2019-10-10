---
author: mdenomy
date: 2012-01-18 00:55:39+00:00
draft: false
title: So Begins The Season of Ruby
type: post
url: /2012/01/17/so-begins-the-season-of-ruby/
tags:
- Ruby
- Season of Ruby
---

I wasn't sure if from my [last post](http://mdenomy.wordpress.com/2011/12/23/i-hate-year-end-lists/), this would be a year of Ruby, a lifetime of Ruby, or 20 minutes of Ruby, so let's start with the notion of a _season_ of Ruby.

[Lao Tzu](http://www.quotationspage.com/quote/24004.html) said "a journey of a thousand miles begins with a single step".  So as much as I would like to embark on this voyage on a shiny new Mac, running TextMate as my editor, I will stick a little closer to my comfort zone and start out running [RubyMine](http://www.jetbrains.com/ruby/) on my Windows machine.  As a .NET developer, I am pretty entrenched in the IDE experience.  That is not to say I don't want a shiny new Mac, but I also don't want to get bogged down as I learn a new language.  The RubyMine experience is very familiar to me since I use Visual Studio with [Resharper](http://www.jetbrains.com/resharper/) and for a mere $69 for a personal license it seems like a no-brainer.

So where to start....

I scoured various blogs and the Ruby docs for good places to learning Ruby.  I settled on starting with the [Ruby Koans](http://rubykoans.com/) site.  I really like that this tutorial had a test-centric approach.  One of the draws to exploring the Ruby community is that testing is baked into the culture.  The Ruby Koans allowed for a lot of experimentation and I tried to take the approach of not just blowing through the problems, but really asking what are they trying to teach in this lesson.  I tried to cause tests to fail in different ways and added some scenarios of my own to try and investigate further.

Another resource was to just use [IRB](http://en.wikipedia.org/wiki/Interactive_Ruby_Shell), the interactive Ruby shell.  Nil is an object, huh?  What methods does it have.  I suppose I could pore through documentation or maybe just...let's see if this works


``` 
irb(main):001:0> nil.methods
=> ["inspect", "&", "clone", "public_methods", "display", "instance_variable_defined?", "equal?", "f
reeze", "to_i", "methods", "respond_to?", "dup", "instance_variables", "__id__", "|", "method", "eql
?", "id", "to_f", "singleton_methods", "send", "taint", "frozen?", "instance_variable_get", "^", "__
send__", "instance_of?", "to_a", "type", "protected_methods", "object_id", "instance_eval", "==", "=
==", "instance_variable_set", "kind_of?", "extend", "to_s", "hash", "class", "tainted?", "=~", "priv
ate_methods", "nil?", "untaint", "is_a?"]
irb(main):002:0>
```
Good gravy, so simple even a .NET developer like me can do it ;)  I found myself playing a lot in the IRB when I wanted to just try something out.

I got though the basics of asserts, objects, nil, and arrays with the koans, diving over to various websites, StackOverflow, irb, and the [Ruby core docs](http://ruby-doc.org/core-1.9.3/) as I ran into questions.  I am using the [Pomodoro technique](http://www.pomodorotechnique.com/) to timebox my activities into manageable chucks and try to stay fresh.

The plan for next time will be to continue with the koans, probably for a while, to build up some core knowledge.  At some point I will dive into the Koans code itself as one of the goals of the last post was to read more code as well as write it.

In my experience, the best way to learn code is to write code, but I also reserved the following books from the library to have around as  references and for tips on style.

* [Programming Ruby](http://www.amazon.com/Programming-Ruby-1-9-Pragmatic-Programmers/dp/1934356085) (aka the pick-ax book)
* [Ruby Best Practices](http://www.amazon.com/Ruby-Best-Practices-Gregory-Brown/dp/0596523009)
* [The Ruby Way](http://www.amazon.com/Ruby-Way-Second-Techniques-Programming/dp/0672328844)

I also want to take a peek at [Why's (Poignant) Guide To Ruby](http://mislav.uniqpath.com/poignant-guide/)
