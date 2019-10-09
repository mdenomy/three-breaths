---
author: mdenomy
date: 2014-01-19 14:31:50+00:00
draft: false
title: Aikido, Controller Tests, and LinkedIn at Launch Academy
type: post
url: /2014/01/19/aikido-controller-tests-and-linkedin-at-launch-academy/
tags:
- Learning
- Rails
---

I had a nice visit the other day speaking at [Launch Academy](http://www.launchacademy.com/).  It's no secret that I am a big fan of the program.  As a community, we need to do more to produce good entry-level developers and also to help them develop their careers.

https://twitter.com/launchacademy_/status/423940556046483456

My talk was geared towards preparing them for what happens when they leave Launch Academy and some of the things they can do to continue learning and growing as software developers.  The three topics: Aikido, Controller Tests, and LinkedIn don't seem to have anything to do with one another, but let's look a little closer.


## Aikido


I don't know the first thing about aikido, but I do know of a [talk that Alistair Cockburn gave](http://www.infoq.com/presentations/cockburn-bury-not-praise-agile) where he talks about aikido and the three stage of learning: Shu, Ha, and Ri.  These stages of learning are common to almost any endeavor, including software engineering.  Right now, the students at Launch Academy are in the _**shu**_ phase, learning a single technique from their masters.

When they go out into the world, they will be exposed to new techniques and new masters, and it is their responsibility to be open to these new techniques, try them out, and incorporate them into their own practices.  This is the _**ha**_ phase.

With some hard work, practice, and luck they may reach the _**ri**_ phase, where they are inventing their own techniques, but that wasn't part of my talk.

I highly recommend the [talk by Alistair Cockburn](http://www.infoq.com/presentations/cockburn-bury-not-praise-agile), it covers so many great ideas about developing your craft.  He is an amazing guy and his talks are always engaging.


## Controller Tests


I have been thinking a lot lately about controller tests in Rails.  What value do they serve, are they still worth writing?  This is probably the subject of another blog post or series of posts, but in the talk I wanted to tie it in with the concept of shu-ha-ri and being open to new ideas.

When I first started learning Rails, one of my primary resources was Michael Hartl's amazing tutorial.  So many of us owe him so much for showing us the way into an awesome framework.  At the time I was learning, I recall the tutorial having a fair number of controller tests, and those tests became part of my _**shu**_ learning phase of Rails.

As I started to develop more Rails apps, and getting exposed to more practices and techniques, I was forced to rethink the role of controller tests.  I found some of the ways I was using them had little intrinsic value.  In some cases, they were essentially testing the framework (e.g. index action rendering index template) or were a mix of controller and view tests that were brittle and not as comprehensive as a Capybara feature spec.

Taking a _**ri**_ approach, I have adapted my practices to do more outside-in tests.  These have the advantage of reinforcing the customer experience and keep me from diving too deep too soon.  They allow me to explore the data relations and behaviors before getting in to specifics about the low-level details.

It is interesting to note that in researching the talk, I could not find many (if any) controller tests in the current edition of Hartl tutorial.


## LinkedIn


The third phase of the talk took a bit of a left turn, but I think is an important lesson for someone trying to break into the field.

I am a big believer in REAL networking, i.e. talking to people, building relationships, asking questions, and following up.  I have made some awesome friends, mentors, and mentees in the Rails community.  It took me too long to learn how to effectively meet people and build relationships.  Fear and imposter syndrome are tough things to overcome.

https://twitter.com/danidewitt/status/424292064319508480

I see a lot of people not networking effectively and it makes me sad.  We had a really good discussion about getting out and talking to people, sending follow up/thank you emails, and personalizing your LinkedIn invites so the person on the other end remembers you and is inclined to accept your invite.  A big key is following up, if you make a contact at a meetup, say hello at the next meetup, ask a question about something they told you about themselves, be genuine.

As always, it was great to meet another Launch Academy cohort.  I hung around for quite a while and the Launchers had awesome questions.  Looking forward to seeing them out in the community soon.

[slideshare id=30110988&style=border:1px solid #CCC;border-width:1px 1px 0;margin-bottom:5px&sc=no]
