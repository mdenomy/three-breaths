---
author: mdenomy
date: 2012-01-21 17:36:33+00:00
draft: false
title: Season of Ruby - Learning the Syntax
type: post
url: /2012/01/21/season-of-ruby-learning-the-syntax/
tags:
- Ruby
- Season of Ruby
---

The [Season of Ruby](http://mdenomy.wordpress.com/category/season-of-ruby/) continues...

I am staying with the [Ruby Koans](http://rubykoans.com/) for now, I really enjoy the layout as I learn the basics of the language and it's syntax.  To this point I have covered asserts, the notion of nil (it really is an object), objects, arrays, hashes, strings, symbols, and my favorite...regular expressions.

I have a love-hate relationship with regular expressions.  Unlike many programmers who may deal with a lot of text, in my world of medical devices and laboratory automation I don't need to rely on regex all that much.  To paraphrase [the most interesting man in the world](http://memegenerator.net/The-Most-Interesting-Man-In-The-World), "I don't always use Regexp, but when I do, it is a powerful, painful, awful, and wonderful experience....every time".

Things that I have found interesting or noteworthy about the most recent koans:

* Array slicing and hashes feel a lot like Python.
* The PERL-inspired "flexible quotes" are interesting and easy to use
* I had a WTF moment with the shovel operator "<<" versus "+=", but I am not alone [there](http://myagileeducation.com/2011/ruby-shovel-operator-what-the/).  After Googling around it made sense and this [article ](http://library.edgecase.com/Ruby/2010/10/31/a-little-more-about-strings.html)about the performance differences was a real eye opener.  I imagined "<<" would be faster than "+=", but wow!
* I want to play around more with heredocs.  Again, nothing Earth-shattering, just not something I have used in my day-to-day programming.  Can see where this would make working with text a lot easier

I was a little confused about Ruby symbols at first.  How do they get "initialized", how do you use them, why don't they take an "=", what can you do with them once you've got them.  After some Googling, things were starting to take shape, but I was still not perfectly clear on them.  But wait....


{{< figure src="http://mdenomy.files.wordpress.com/2012/01/dangermouseirb.jpg?w=450" title="Off to the REPL" >}}

_NB: I realize if [SOPA ](http://en.wikipedia.org/wiki/Stop_Online_Piracy_Act)were to pass as is I could go to jail for this [Dangermouse ](http://en.wikipedia.org/wiki/Danger_Mouse_(TV_series))cartoon, but it is such a hack job by me, maybe I should..._

I really love the ability to play around with ideas in a [REPL](http://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop).  [Verdammelt ](http://verdammelt.posterous.com)had an interesting article about using a [REPL and TDD](http://verdammelt.posterous.com/tdd-and-repl-analogies) and this seemed like a perfect place for some experimentation.  I was able to pretty quickly satisfy my curiousity and questions about Ruby symbols in the IRB.  I thought it was neat how one answer may lead to another question and so on...very exploratory.

Which brings us to the aforementioned regular expressions.  Some people love regular expressions.  Some people can whip a regex out of thin air to find the middle names of everyone with a blue house, between the ages of 38-43, with 2 dogs OR 1 ferret and 3 parrots.  I am not one of those people.  I always liked this [joke](http://regex.info/blog/2006-09-15/247)


<blockquote>
Some people, when confronted with a problem, think
“I know, I'll use regular expressions.”
<br/>
<br/>
Now they have two problems.
</blockquote>


But interestingly I had an "a ha" moment while doing the Regexp exercises.  It wasn't some "the skies opened and I know all Regexp syntax by heart now".  That unfortunately did not happen.  It was that it reinforced this notion of [TDD](http://mdenomy.wordpress.com/2011/01/15/introduction-to-test-driven-development-at-nashua-scrum-club/):


<blockquote>
A well-written test suite _IS_ documentation.
<br/>
A well written test suite _IS_ a specification.
</blockquote>


I love that about [TDD ](http://mdenomy.wordpress.com/2011/01/15/introduction-to-test-driven-development-at-nashua-scrum-club/)and it is one of the reasons I am having so much fun with the Ruby Koans.  Every test clearly expresses a single, intended behavior.

Stay tuned for a [retrospective ](http://mdenomy.wordpress.com/category/retrospectives/)on the first iteration, and if you have tips on good Ruby resources I would love to hear them.
