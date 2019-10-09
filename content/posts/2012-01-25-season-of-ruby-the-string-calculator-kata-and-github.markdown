---
author: mdenomy
date: 2012-01-25 19:30:03+00:00
draft: false
title: Season of Ruby - The String Calculator Kata and GitHub
type: post
url: /2012/01/25/season-of-ruby-the-string-calculator-kata-and-github/
tags:
- GitHub
- Ruby
- Season of Ruby
---

Last[ iteration](http://mdenomy.wordpress.com/2012/01/22/season-of-ruby-iteration-zero-retrospective/) I realized that I needed to start writing some code, so the big story for this iteration was to do Roy Osherove's [String Calculator Kata](http://osherove.com/tdd-kata-1/) and also to push the code up to [github](https://github.com/mdenomy). [Mission accomplished](https://github.com/mdenomy/StringKata)! But unlike 'W' standing on the aircraft carrier, I know there is a lot more work to do.

I used [git](http://git-scm.com/) a little bit a few years ago, and initially it was a painful adjustment because all my past experience was with centralized repositories like Subversion, Team Foundation, and CVS. Distributed repositories were a paradigm shift, but after some getting used to it really started to grow on
me. I loved home easy it was to create branches and that developers could work on different features in isolation before bringing their code back into the "trunk". So it was great to get some code up on github, using both the RubyMine integration and plain old git command line tools. I need to spend a little time refamiliarizing myself with the terminology and workflow, but it was a great start.

As far as the kata goes I feel similarly. Did everything turn out exactly the way I wanted? No, but it is a kata. You do it, you learn something, you take those lessons forward, and you move on. Maybe I will do it again in a few weeks and see how the outcome is different. It served it's purpose in getting me out of my comfort zone and writing code in a new language. It also got me asking new questions and places to take the journey. Some of the things that I wondered about as I was doing the kata



	  * Does Ruby have the philosophy that there is one "right and obvious" way to do things, ala Python, or is it more Perl-like in that there are a [many ways](http://c2.com/cgi/wiki?ThereIsMoreThanOneWayToDoIt) that are acceptable and it is a developer choice. At least according to this [page ](http://c2.com/cgi/wiki?PythonVsRuby)it seems to borrow from Perl in that there is more than one way to do it.
	  * How do private and protected variables/methods work in Ruby?  Are they often used or are there other patterns that are applied?  I remembered with Python that the notion of "private" was downplayed, at least with what I saw. I am not a Python expert so I may be mis-representing here.
	  * Are instance variables used much?  In one of my refactorings I noticed that I was passing the same argument to a lot of methods, and decided to keep it in an instance variable. Was that Ruby-esque? Was it habits from .NET creeping in?  Was it the "best" solution

I don't know the "Ruby Way" yet, so these questions are all the more reasons to start looking at OPC (other people's code). So it is probably time to fork a Ruby open source project and start playing around with it.

I want to make sure I keep writing code too, so I think I will take a time-boxed stab at [Conway's Game of Life](http://en.wikipedia.org/wiki/Conway's_Game_of_Life). I had a lot of fun with that at the [Global Day of Code Retreat](http://blog.coderetreat.com/global-day-of-coderetreat). I want to time-box it because it is something that I could spend a lot of time on, depending on how far I want to take it, and I am not looking for a complete solution but to exlore some different ideas in code. Maybe it's time to start thinking about bring [Rails](http://rubyonrails.org/) into the mix too.

All these ideas make me think I should be keeping a formal backlog and continuing with the notion of treating this journey as an Agile project. I use a tool called [Rally](http://www.rallydev.com/product-features/rally-community-edition) at work, maybe I'll use that or investigate another tool. Any ideas or recommendations from the blogosphere?
