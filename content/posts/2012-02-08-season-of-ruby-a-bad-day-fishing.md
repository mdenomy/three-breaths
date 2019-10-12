---
author: mdenomy
date: 2012-02-08 13:35:57+00:00
draft: false
title: Season of Ruby - A Bad Day Of Fishing
url: /2012/02/08/season-of-ruby-a-bad-day-fishing/
tags:
- Rails
- Ruby
- Season of Ruby
---

I have been really excited to get going with Michael Hartl's [Ruby on Rails Tutorial](http://ruby.railstutorial.org/chapters).  Skimming through the table of contents and the introduction, I liked that he makes testing such a focal point of the tutorial.  I also liked the [Comments for Various Readers](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book?version=3.2#sec:comments_for_various_readers) section.  I fit into the "Experienced programmers new to web development" camp, and after reading the introduction I knew  that this would be a great tutorial for me.

The first section was well laid out, and focused on getting your environment set up.  It also touched on using [git ](http://git-scm.com/)and [github ](https://github.com/)which is starting to feel like old hat for me, but then it ended with deploying the sample app to [heroku](http://www.heroku.com/) which was a new thing for me.  As someone experienced in software development, but new to web development, it was great to have the heroku deployment so well explained and easy to do.  I was feeling quite full of myself.

Then came the 2nd chapter...

Someone once said "A bad day fishing is better than a good day at work".  Oh yeah, tell that to [Captain Quint](http://www.imdb.com/character/ch0175379/quotes), he looks like he is having a pretty bad day fishing.

{{< figure src="/images/quint.jpg" title="A Bad Day Of Fishing" >}}

Now you could argue that he's actually just having a good day at work, since technically, as a fisherman, he is at work.  But I digress. Up to this point my Ruby experience has been all pie and ice cream, but today was a bad day of fishing with Ruby.

The author [goes to great length](http://ruby.railstutorial.org/chapters/beginning?version=3.2#sec:rubygems) to explain that the tutorial uses an older more stable combination of Rails/Ruby versions and that is what you should install.  But I am _sooooooo_ much smarter than that and besides, I want to use the newest stuff.  To say the least, I ran into a lot of problems with getting the right combinations of Ruby, Rails, sqlite, etc, etc working.  I learned a lot about [gems ](http://rubygems.org/)and [bundler ](http://gembundler.com/)along the way.  I think things were further complicated by running on a Windows box as well.

After a lot of time fighting my environment, I realized I was fighting the wrong battle and the smart thing to do was to get the environment set up as the author intended to be able to get the most out of the tutorial.  Once I made that decision I was back on the happy path and am looking forward to moving on to more in-depth parts of the tutorial.  I don't feel like it was a wasted experience, because I did learn quite a bit digging around.  I imagine this can be a significant issue for Rails projects, especially as new versions of Rails, Ruby, or different gems roll out and that the correct dependencies need to be addressed.  It reminded me a lot about the "[DLL Hell](http://en.wikipedia.org/wiki/DLL_Hell)" days of Windows before .NET.

The take-away is if you decide to do[ this tutorial](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book) follow the author's advice and set up the environment as specified.  The lessons to be learned are more to the core of Rails and running the latest version of Rails or the application's dependencies is not important.  And now that I am on the right track I am looking forward to moving on to more advanced sections of the tutorial.
