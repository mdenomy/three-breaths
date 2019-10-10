---
author: mdenomy
date: 2010-10-21 16:43:55+00:00
draft: false
title: A Test That Isn't Automated Is a (fill in the blank)
type: post
url: /2010/10/21/a-test-that-isnt-automated-is-a-fill-in-the-blank/
tags:
- MbUnit
- mocks
- TDD
- testing
---

Recently I ran into some problems with tests that could not easily be run in an automated manner.  In the spirit of a glass half full, I am trying to decide if manual tests are partially useful, partially useless, or totally useless.

The kind of work that I do, [laboratory automation](http://www.helicosbio.com/Products/HelicosregGeneticAnalysisSystem/HeliScopetradeSequencer/tabid/87/Default.aspx), scientific instrumentation, medical devices, deals a lot with hardware: sensors, motors, lasers, all kinds of fun stuff.  Over the last several years I have relied heavily on [TDD](http://c2.com/cgi/wiki?TestDrivenDevelopment), [DI](http://martinfowler.com/articles/injection.html), and [mocking frameworks](http://martinfowler.com/articles/mocksArentStubs.html#TestsWithMockObjects) to be able to abstract away many of the dependencies on the actual hardware for my testing and instead use mocks to verify higher level control functions.

At some point the rubber needs to meet the road and you need to make sure that what you are doing with the hardware is really what is supposed to happen, i.e. did a motor move, was an image captured, did you really measure the temperature correctly.  I have found that the ease-of-use of modern testing frameworks like [MbUnit ](http://www.mbunit.com/) make writing a test a convenient way to perform this kind of hardware-software integration test.  As an example, consider a test that verifies that a motor moves correctly.  The test will read the position of the motor, move the motor in the forward direction, stop the motor, then read the position again and see if the motor has moved.

``` cpp
        [TestCategory("Motor Hardware Tests")]
        [TestMethod]
        public void TestMovingMotorForward()
        {
            double moveMillimeters = 10.0;
            double allowedTolerance = 0.1;
            LinearMotor motor = new LinearMotor();
            double startPosition = motor.GetPosition();
            motor.MoveRelative(moveMillimeters);
            double endPosition = motor.GetPosition();

            Assert.AreEqual(moveMillimeters, endPosition - startPosition, allowedTolerance);
        }
```

Now this test is doing a lot of things and it certainly is not a unit test in the strictest definition.   I want to stress that before I ever get to this kind of test I have already written a lot of lower level unit tests with the hardware abstracted away.  In many cases the code has been written and unit-tested long before the hardware even gets in the door and gets wired up, so these types of tests are really more like system integration tests.

But here's the problem.  I can't run this test on my automated build server because the test requires a special fixture, i.e. the hardware.  I can exclude the test by including it in a special test category and telling my automated test runner to not execute that category, but what do I do about running the test?  Do I make sure to run it manually at some frequency (1/week, 1/day, etc).  Do I just leave it in the code base and only run it manually if there is a reported problem?  What happens when I run it and there is a problem, how to I know when the error got introduced?  Do I rip the test out since it is not automated and is just [cruft](http://en.wikipedia.org/wiki/Cruft)?

After some recent experiences of having problems occur and not knowing when they were introduced, I am really leaning heavily towards the notion of setting up a special build platform that is able to run several types of hardware tests.  Tests like these can take a long time to run due to the delays associated with the hardware, so it is not realistic to run them on every check-in, otherwise any hope at the [10 minute build](http://jamesshore.com/Agile-Book/ten_minute_build.html) is out the window.  But you could certainly set up a build to run once a day, or on the weekend, or at some frequency that works for you.

Now you may not have test problems just like this, i.e. hardware related, but maybe you have some integration tests that are long running tests.  Maybe you want to test how a database runs under extended load or you have some other stress test.  Find a way to make sure that the tests are automatically executed at some frequency, otherwise you are inviting the time when you go to run a "manual" test, only to find that it has long since stopped working.

My take-away is that if a test is not automated at some meaningful frequency it should be removed from the code, because it is not doing what you need it to do and if it is not being run it is just more technical debt.
