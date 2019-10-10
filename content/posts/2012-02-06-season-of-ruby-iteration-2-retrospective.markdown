---
author: mdenomy
date: 2012-02-06 04:07:53+00:00
draft: false
title: Season of Ruby - Iteration 2 Retrospective
type: post
url: /2012/02/05/season-of-ruby-iteration-2-retrospective/
tags:
- Season of Ruby
---

Things are coming together well with the[ Season of Ruby](http://mdenomy.wordpress.com/category/season-of-ruby/).  Getting out of my comfort zone was a driving theme and there has been some discomfort, but I am now establishing a new comfort zone, familiarizing myself with a new language and new tools.  There is still a lot of work to do, but I am really pleased with how things are going.  And with that, on to the retrospective.

**What Went Well**

* Got to write more code this iteration.  I wrote a [Ruby implementation of Conway's Game of Life](https://github.com/mdenomy/GameOfLife).  I really love to code and sometimes I don't get to do that enough in my day job.  Solving a problem was a lot of fun.
* I stayed true to TDD, which is my standard way of working, but given the new tools it is important to stay true.  So far I have been using test-unit, but I also got a look at some [RSpec](http://rspec.info/).
* Played around with forking a project on github, starting to get more comfortable with the workflow.

**What Can Be Improved On**

* I hit a roadblock with TDD when I got to a point where in .NET I would use a mocking framework.  The reason I wanted to mock was because I was interested in testing behavior and not state.  I wanted to know that the GameOfLife class was interacting with the Cell class in the correct sequence.  Need to understand how that type of testing would be done under Ruby.
* I need to understand how to structure my projects in Ruby.  That will mean looking at more code and also learning tools like Rake.
* Start thinking about the overall roadmap of this adventure.  I'm into it far enough now that I am starting to feel comfortable with the tools, now it is time to start doing some longer range (1-2 month) planning.

**What Am I Going To Do To Improve Things**

I still have some work on Ruby fundamentals, but I would like to get a simple Rails project under my belt to give me some context and also to start the long term thinking.  I was considering the [Ruby on Rails Guides](http://guides.rubyonrails.org/getting_started.html), but now think I will take a crack at [Michael Hartl's](http://ruby.railstutorial.org/chapters/a-demo-app) tutorial.  It seems a little richer and also seems to really focus on testing.

**Iteration 3 Stories**

"Stories" is a reach this iteration.  I am back into uncharted waters with Rails.  I don't know what I don't know yet.  Instead I will just put in at least 6 hours on  [Michael Hartl's](http://ruby.railstutorial.org/chapters/a-demo-app) tutorial
