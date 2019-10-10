---
author: mdenomy
date: 2012-02-12 23:02:23+00:00
draft: false
title: Halftime Review of Michael Hartl's Ruby on Rails Tutorial
type: post
url: /2012/02/12/halftime-review-of-michael-hartls-ruby-on-rails-tutorial/
tags:
- Rails
- Ruby
- Season of Ruby
---

I am a newcomer to [Ruby](http://www.ruby-lang.org/en/) and [Ruby on Rails](http://rubyonrails.org/), so when I wanted to get started with Rails I looked around quite a bit for a good starting point.  I finally settled on [Michael Hartl's Ruby on Rails Tutorial](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book).  I am about halfway through with the tutorial, and I am really pleased so far.  This is a great tutorial for a lot of reasons, but the aside from just teaching Rails, he is also teaching good development practices such as:

* How to use [git](http://git-scm.com/) effectively.  The tutorial starts out with git basics and then quickly moves on to integration with [github](https://github.com/), working on branches when adding new features, and merging changes back into the master.
* Focus on testing.  We start out with [RSpec](http://rspec.info/) writing unit tests, but then also add in integration tests.  He also follows a TDD approach for a lot of the tutorial where the tests come before the code, a practice that I believe strongly in.
* Stresses good developer practices like running your tests before and after merging a branch.  Sure the merge probably went fine, but be a good citizen and test it before you push it up to github.
* Refactoring your code to reduce duplication and make it more readable and maintainable.
* Shows how to deploy your code up to [heroku](http://www.heroku.com/)
* Introduces real world work practices like [sketches and wireframes](http://ruby.railstutorial.org/book/ruby-on-rails-tutorial#sec:structure).

The focus on testing, refactoring, and general good developer practices is important to me.  These are practices that I have been using for a long time, but it is great to see them so much a part of Ruby on Rails.  Just seeing that standard project hierarchy includes a place for tests tells you it is ingrained in Rails.  I really loved this quote from the tutorial

<blockquote>
If you ask five Rails developers how to test any given piece of code, you’ll get about fifteen different answers—but they’ll all agree that you should definitely be writing tests
</blockquote>


As far as the Rails side of the tutorial goes, I think after my[ initial environment snafu](http://mdenomy.wordpress.com/2012/02/08/season-of-ruby-a-bad-day-fishing/) (that's all on me), things have been going great.  I am starting to see more of how Rails implements [MVC](http://ruby.railstutorial.org/chapters/a-demo-app#sec:mvc_in_action).  MVC is obviously not a new concept, it's been around for a [while](http://c2.com/cgi/wiki?ModelViewControllerHistory), but each framework and environment uses it differently.  I also really enjoy the ordered structure of a rails project and can see what an advantage it is to have this kind of common project structure.  I know ASP.NET MVC also tries to use a [standard project hierarchy](http://msdn.microsoft.com/en-us/library/dd410120.aspx), but rails felt a little cleaner and more intuitive.

After some simple applications to get your feet wet and make sure your environment is good to go, the tutorial uses a micro-blogging application to slowly walk through the different capabilities in rails.  The tutorial also explains some of the "magic" that goes on under the covers that Rails provides for you.  This has encouraged me to[ route around](http://guides.rubyonrails.org/routing.html) (pun intended, thanks) to understand more of the magic.  Aside from routing, we have also hit a bit on database integration and [migrations](http://ruby.railstutorial.org/chapters/modeling-and-viewing-users-one#sec:database_migrations), [some CSS](http://ruby.railstutorial.org/chapters/filling-in-the-layout#sec:custom_css), and [partials](http://ruby.railstutorial.org/chapters/filling-in-the-layout#sec:partials).

One thing this tutorial will not teach you is a lot of Ruby, and the author is [quite clear about that](http://ruby.railstutorial.org/book/ruby-on-rails-tutorial#sec:comments_for_various_readers).  He provides some good references for learning more Ruby, but the focus here is on Rails, and he keeps the amount of Ruby necessary to a minimum.

I am about halfway through and am hoping to finish up in the next 2 weeks.  It is a little slow going because as I learn I often go off to investigate different aspects of what I am learning.  Finishing the tutorial will not be the end of the journey, but it certainly has helped get it going in a good direction.  I recommend it highly to anyone interested in getting started with Ruby on Rails.
