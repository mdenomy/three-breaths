---
author: mdenomy
date: 2008-02-11 21:48:34+00:00
draft: false
title: Rethinking the C# using statement
type: post
url: /2008/02/11/rethinking-the-c-using-statement/
tags:
- C#
- mocks
- nmock
---

I've typically used the C# using construct to wrap an instance on an object that has a short lifetime and requires a call to Dispose.  The using keyword hides the need to call Dispose explicitly and avoids having to use a try-finally to ensure that Dispose is always called.  One example of a class that I often use the using keyword is a stream class

[sourcecode language="cpp"]
        using (FileStream fs = File.Create(path))
        {
            // Do something with the file stream
            ...

        }  //  Dispose gets called automatically here
[/sourcecode]


Recently, while using [NMock2](http://nmock.org/), I came across a usage of the using statement that forced me to stop and think about what was going on under the covers.  [NMock2 ](http://nmock.org/)is a [mocking framework](http://en.wikipedia.org/wiki/Mock_Object) and   the Order/Unordered properties are used to tell the framework whether you care that the expectations are satisfied in a particular order.  The Ordered attribute tells NMock2 that the expectations must match the actual order of execution, while Unordered indicates that all the expectations must be satisfied, but the order doesn't matter.  When you are defining the expectations you put the Ordered/Unordered attributes in a using statement.  They can even be nested, so a test might look something like this (and no I don't use class/method names like this):

[sourcecode language="cpp"]
        [Test]
        public void CanDoIt()
        {
            using (_mockery.Ordered)
            {
                Expect.Once.On(_thing1).Method("Method1").WithNoArguments();

                using (_mockery.Unordered)
                {
                    Expect.Once.On(_thing1).Method("Method2").WithNoArguments();
                    Expect.Once.On(_thing1).Method("Method3").With(foo, bar);
                }

                Expect.Once.On(_thing1).Method("Method4").WithNoArguments();
            }

            classUnderTest.DoIt();
        }
[/sourcecode]


In the above test we are telling NMock that we expect the following methods to be done in a certain order.  Method1 should be called first, followed by Method2 and Method3 in any order, followed by Method4.

Using NMock2 for unit testing can be the subject of another post, but it was the use of the Ordered/Unordered attributes inside of a using statement that really made we think about what was going on.  What I found intriguing about the use of this construct is that the Ordered/Unordered properties are returning an object that implements IDisposable but you never do anything with the returned property.  NMock2 is using the using contruct with Ordered and Unordered as [syntactic sugar](http://en.wikipedia.org/wiki/Syntactic_sugar) to make the test cases easier to read, and I think it works well in NMocks case.

Under the covers, the constructor of the object returned from the Ordered/Unordered properties is actually being used to set state in the underlying owning Mockery object.  I don't think I can show only a snippet of the NMock2 source code under the license agreement of the NMock2, but if you want to see for yourself what it is doing you can download it from [here](http://sourceforge.net/projects/nmock2/).

Basically the object that gets created by the Ordered/Unordered properties takes a reference to the "parent" object in the constructor.  In this case the parent object is the Mockery object.   The Dispose method cleans up the state in the parent object.  I came up with a somewhat contrived package shipping class that does something similar to what NMock is doing as an example, although in my example you can not nest using statements like in NMock.

[sourcecode language="cpp"]
using System;
using System.Collections.Generic;
using System.Text;

namespace TestUsing
{
    class Program
    {
        static void Main(string[] args)
        {
            PrioritizedShipping shipping = new PrioritizedShipping();

            // Setup a bunch of packages for priority
            using (shipping.Overnight)
            {
                shipping.ScheduleForDelivery(new Package(10.0, 51.2));
                shipping.ScheduleForDelivery(new Package(11.0, 52.3));

                // Note you can not nest usings because there is no Push/Pop mechanism implemented
            }

            // Default is standard shipping, could also use a using( shipping.Standard)
            shipping.ScheduleForDelivery(new Package(300.0, 1248.0));

            // For this example I prefer a more straightforward method that is clear to a manintainer
            shipping.ABetterScheduleForDelivery(new Package(500.0, 2448.0), ShipPriority.Standard);
            shipping.ABetterScheduleForDelivery(new Package(20.0, 12.0), ShipPriority.Overnight);
            shipping.ABetterScheduleForDelivery(new Package(21.0, 13.0), ShipPriority.Overnight);
        }
    }

    public class Package
    {
        private double _weight;
        private double _girth;

        public Package(double weight, double girth)
        {
            _weight = weight;
            _girth = girth;
        }
    }

    public enum ShipPriority { Overnight, Standard };

    public class PrioritizedShipping
    {
        private List<Package> _priorityPackages = new List<Package>();
        private List<Package> _standardPackages = new List<Package>();
        private List<Package> _activeList;

        public IDisposable Overnight
        {
            get { return new SetupShippingHelper(this, ShipPriority.Overnight); }
        }

        public IDisposable Standard
        {
            get { return new SetupShippingHelper(this, ShipPriority.Standard); }
        }

        public void SetupPriority(ShipPriority priority)
        {
            if (priority == ShipPriority.Overnight)
                _activeList = _priorityPackages;
            else
                _activeList = _standardPackages;
        }

        public void ScheduleForDelivery(Package package)
        {
            _activeList.Add(package);
        }

        public void ABetterScheduleForDelivery(Package package, ShipPriority priority)
        {
            if (priority == ShipPriority.Overnight)
                _priorityPackages.Add(package);
            else
                _standardPackages.Add(package);
        }

    }

    public class SetupShippingHelper : IDisposable
    {
        PrioritizedShipping _parent;

        public SetupShippingHelper( PrioritizedShipping parent, ShipPriority priority )
        {
            _parent = parent;
            _parent.SetupPriority(priority);
        }

        #region IDisposable Members

        public void Dispose()
        {
            _parent.SetupPriority(ShipPriority.Standard);
        }

        #endregion
    }
}
[/sourcecode]


Note in the contrived example I've come up with I think it is actually less clear and I prefer a more explicit method, _ABetterScheduleForDelivery_, to indicate what priority to use.  I would also have some serious concerns about how something like this would work in a multi-threaded environment.  I can see how you could make it work, but at the end of the day I think this type of approach would be harder to maintain and could have some unforeseen consequences.  I think it works really well for the NMock2 case, but I would have to think long and hard before using it in my own code.

I haven't found a use for this particular usage of the using statement, but it does give me something to think about and a tool that perhaps I can use in the future.  I think there is a lot to be said for code that reads well, but that also needs to be balanced against a maintainer being able to understand what is happening under the covers to avoid inadvertent consequences.
