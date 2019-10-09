---
author: mdenomy
date: 2012-02-04 12:24:36+00:00
draft: false
title: Season of Ruby - You'll Always Remember Your First Fork
type: post
url: /2012/02/04/season-of-ruby-youll-always-remember-your-first-fork/
tags:
- Season of Ruby
---

Forking the [cocaine project](https://github.com/thoughtbot/cocaine) gave me a chance to see a little bit more of Ruby style, at least with an ‘n of 1’.  The goal wasn't to make any sweeping changes, just get it to run, see some of the style and implementation choices, and break through another barrier, i.e. forking a project on github.  Some of the things I took away from the exercise:

Keeping code lined up by column seems to matter from a style perspective:

[sourcecode language="ruby" gutter="false"]
def initialize(binary, params = "", options = {})
   @binary            = binary.dup
   @params            = params.dup
   @options           = options.dup
   @logger            = @options.delete(:logger) || self.class.logger
   @swallow_stderr    = @options.delete(:swallow_stderr)
   @expected_outcodes = @options.delete(:expected_outcodes)
   @expected_outcodes ||= [0]
end
[/sourcecode]

I have followed this style in the past, but found it a pain to maintain. Not a _huge_ pain, but you have to rearrange the whole set if you add something longer than what is already in there. I'll keep poking around open-source projects to see if this style is prevalent, but it is not something I am militant about. I treat these type of style issues as you want to be consistent throughout the code, so if that is the way a project does it, that is the way you should do it.

Got a look at the [begin/rescue/ensure](http://ruby-doc.org/docs/ProgrammingRuby/html/tut_exceptions.html) syntax for exception handling, which is pretty similar to [try/catch/finally](http://msdn.microsoft.com/en-us/library/dszsf989(v=vs.80).aspx) in C#.  As I see the two languages side-by-side after I put those links in, somehow the Ruby feels more "natural" and easier to read.  Huh, have I already [taken the red pill](http://en.wikipedia.org/wiki/Red_pill_and_blue_pill).

Got a taste of [RSpec](http://rspec.info/), which was good because to this point I have been using test-unit, and I have been really curious to see what other testing options are available in Ruby and where you would use one versus another.  It certainly looks more descriptive and seems something of a more fluent syntax, although I am surprised lines like these

[sourcecode language="ruby" gutter="false"]
  lambda { cmd.command }.should raise_error(Cocaine::CommandLineError)
  output.should match(%r{/path/to/command/dir})
[/sourcecode]

Aren’t actually like these, i.e. the use of the ‘.’ is consistent

[sourcecode language="ruby" gutter="false"]
  lambda { cmd.command }.should.raise_error(Cocaine::CommandLineError)
  output.should.match(%r{/path/to/command/dir})
[/sourcecode]

Regardless, I have heard good things about RSpec and it is on my list of things to look at.  I am really excited about looking at different testing techniques with Ruby, especially [BDD ](http://cukes.info/)testing.

I had to futz around a bit with the [rakefile ](http://rake.rubyforge.org/)to get it to run.  It was all path related issues due to running on a Windows box.  I’m sure if I wanted to put more into it I could have come up with a cross-platform, but that wasn’t the goal of the exercise.  Besides it just gives me more reason to treat myself to a Mac.

So again, another barrier broken through on the [Season of Ruby](http://mdenomy.wordpress.com/category/season-of-ruby/).  Next github challenge will be to find a project that I can actually contribute to, so fork it, make some changes, [generate a pull request](http://help.github.com/send-pull-requests/), and see those go back into the original project.

P.S. Don't tell the [cocaine project](https://github.com/thoughtbot/cocaine) they weren't really my first fork.  My first was actually the [Spoon-Knife](https://github.com/octocat/Spoon-Knife) project.  But that fork was over so quickly I barely knew what happened.
