---
author: mdenomy
date: 2013-01-16 11:18:39+00:00
draft: false
title: Getting Started with Rails Testing
url: /2013/01/16/getting-started-with-rails-testing/
tags:
- Rails
- TDD
- testing
---

I gave a presentation at the January 2013 Boston Ruby Project Night on "Getting Started with Rails Testing".

{{< youtube Im1lyxSZEu4 >}}

This talk aims at understanding the development workflow while using TDD and the [Red-Green-Refactor](http://www.jamesshore.com/Blog/Red-Green-Refactor.html) loop.

We look at the different test types that you can write in a Rails application

* Unit tests
* Controller tests
* Integration tests

We also look at some of the tools and frameworks that are available for testing, including [RSpec](https://www.relishapp.com/rspec), [MiniTest](https://github.com/seattlerb/minitest), [Test-Unit](http://test-unit.rubyforge.org/), [Capybara](https://github.com/jnicklas/capybara), and [FactoryGirl](https://github.com/thoughtbot/factory_girl_rails).

A simple example is used to show the test-driven development workflow.  The code for the example is on github at https://github.com/mdenomy/expense_tracker.

The github repository uses branches to capture a series of snaphots in the test-driven-development workflow.  See the [Readme](https://github.com/mdenomy/expense_tracker/blob/master/Readme.md) file for a list of the branches, or run the "git branch -a" command to see the full list from the terminal.
