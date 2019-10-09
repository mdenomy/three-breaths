---
author: mdenomy
date: 2010-09-07 00:41:15+00:00
draft: false
title: TDD with C++
type: post
url: /2010/09/06/tdd-with-cpp/
tags:
- mocks
- TDD
- testing
- Unit Testing
---

I know, it is 2010, and doing TDD with C++ probably isn't trending too high on anyone's hot topics list, but after a 8 year hiatus I find myself doing some Agile consulting with an embedded systems team that is using C++.   At first I was concerned about the transition.  What was I going to do without my testing frameworks, my mocking frameworks, my continuous integration support, my...wait I have to manage my own memory too...

Well it is not all bad news folks, a lot has happened in the world of C++.  And while the tools are not yet at the level you may be accustomed to coming from C#, Java, or Ruby, it's not all bad news.  This is not your father's C++.


## Testing Frameworks


There are a few testing frameworks out there for C++: [CppUnit](http://cppunit.sourceforge.net/doc/lastest/index.html), [CxxTest](http://cxxtest.tigris.org/), and [GoogleTest](http://code.google.com/p/googletest/) are some of the better known frameworks.  These three are all heavily influenced by JUnit, so if you are familiar with JUnit, NUnit or even MSTest, you will be familiar with the terminology, i.e. they support test fixtures, have setup and teardown support etc.

On the project I am on, we are using GoogleTest and it is working OK for us.  It can be targetted to a variety of compilers and OS's, so you may have some work to do to get it up and running.  The syntax relies heavily on macros, which isn't all that surprising, but it makes it a little ugly to look at, but it supports the notion of assertions, test fixtures, setup/teardown that you are probably familiar with.  A few simple tests might look something like this

    
    // Tests that 1 really equals 1.
    // Just looking to see if my framework does what I think it does
    TEST(DumbTest, Checks1Is1) {
      EXPECT_EQ(1, 1);
    }
    
    // Tests that a person can be created with a first and last name
    TEST(PersonTests, PersonFullName){
    	Person aPerson = Person("Fred", "Flintstone");
    	ASSERT_STREQ( "Fred Flintstone", aPerson.FullName() );
    }




### Test Output


To get your tests results reported as part of your continuous integration process, you will want to see what output formats the testing framework provides.  GoogleTest supports several output formats, including a text based output that is helpful from running within the IDE as well as an XML report that conforms to the Ant/JUnit format.  We are using TeamCity, so reporting automated test results is straightforward in that regard.


### Controlling What Tests Run


This is an area that hurts a bit, at least if you are coming from an environment where you are used to being able to easily control which tests run while you are in the IDE via a plug-in, for example right-click and select "Run this test" or "Run this test suite".  GoogleTest does have options to control what tests run and which tests do not run, the ability to repeat the test, etc, but it is all via switches to the test runner, which makes the development cycle a little slower.   Since I am using this on an embedded systems project, some tests may  require hardware that is not at the development station or a build  server. To have the test runner skip tests that have the word Hardware in the test name, you would pass **--gtest_filter=-*.*Hardware***.  Although it is a bit cumbersome, at least the capability exists to control which tests run.


## Mocking Frameworks


I am a big fan of mocking frameworks in C#.  I know they are just one tool in the unit testing toolbag, but I find them invaluable for testing interactions between components and can free me from having to write more sophisticated simulators.  [GoogleMock ](http://code.google.com/p/googlemock/)provides mocking support for C++ and like GoogleTest can be targeted towards a variety of development tools and OS's.  Note that as of this writing, there are some problems building GoogleMock for VS2010.

Coming up to speed on any mocking framework takes effort, especially once you get away from the plain vanilla mock scenarios and get into events, custom matchers, custom actions, etc.  Most of my C# mocking is with NMock2, there are other great mocking tools out there, like [TypeMock](http://www.typemock.com/), [RhinoMocks](http://www.ayende.com/projects/rhino-mocks.aspx), and [Moq](http://code.google.com/p/moq/).  If you are used to those tools, you are going to find GoogleMock a little clumbsy and cumbersome, in my opinion.  For example, this snippet sets an expectation that the mutator's Mutate funtion will be called with true as the first argument and a don't care on the second argument (indicated by the '_').  It will also perform an action when the expectation is satisfied by setting the value of the first argument (0-based) to 5

    
      MockMutator mutator;
      EXPECT_CALL(mutator, Mutate(true, _))
          .WillOnce(SetArgumentPointee<1>(5));


Again, like GoogleTest, heavily macro-based and in my opinion a little....clumsy.  Maybe it is just getting used to being in C++ again, but it doesn't flow as naturally as some of the C# mocking tools.  But on the plus side, at least there is a mocking framework andit will probably do 90% of what you need out of the box.  If you need to write a custom action, there may be some work there.


## Other Niceties




### Boost C++ Libraries


Ah memory management, how I have NOT missed you all these years.  Fortunately the [Boost C++ Libraries](http://www.boost.org/) have good support for [smart pointers](http://www.boost.org/doc/libs/1_42_0/libs/smart_ptr/smart_ptr.htm) which relieve the developer of a lot of the pain of memory management.  Not all of the pain, but enought to merit using them.  In addition to smart pointers, the Boost library has a variety of classes for string and text, containers, iterators, math, threading, and on and on.  If your OS or compiler does not directly support something, check the Boost documentation before you implement something from scratch.  Chances are it may have been solved already.


### IOC/DI Tools


Although I have not had a chance to use it yet, there is at least on IOC container tool in C++, [Pococapsule](http://code.google.com/p/pococapsule/).  Since I haven't had a chance to use it yet, I will leave it as an exercise to the reader to try it out, and if you have used it, please feel free to comment on it.


## Summary


Although many of us may not have used it in many years, C++ is still chugging along and has a place in the software universe.   In certain areas it is the best choice based on criteria like performance, foot-print, etc.  It is encouraging to see TDD practices and tools that started in other frameworks/languages come into C++.  They may not have the same ease of use as the other frameworks, but these frameworks also had some warts in their early development.  The open-source aspect of these tools will also hopefully continue to move the feature set and usability of these tools forward.

If I had my choice, I would prefer to be develop in C#, Python, Ruby, or Java.  The ease of use and richness of tools make these more "productive" developer environments, especially when looked at from the perspective of TDD.  However sometimes C++ is the right tool and I am glad to see that the tools are there to develop code in a TDD manner.  They may not be at the level of the tools we are used to, but they are available to us.

And many thanks to the folks on these open-source projects who have put those tools out there.
