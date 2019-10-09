---
author: mdenomy
date: 2008-02-28 20:27:03+00:00
draft: false
title: Using the Automatic Recovery Features of Windows Services
type: post
url: /2008/02/28/using-the-automatic-recovery-features-of-windows-services/
tags:
- .NET
- C#
- Software
- Visual Studio
---

Windows Services support the ability to automatically perform some defined action in response to a failure.  The recovery action is specified in the Recovery tab of the service property page (which can be found in Settings->Control Panel->Administrative Tools -> Services). The Recovery tab allows you to define actions that can be performed on the 1st failure, 2nd failure, and subsequent failures, and also provides support for resetting the failure counters and how long to wait before taking the action.  The allowed actions are



	  * Take No Action (default)
	  * Restart the Service
	  * Run a Program
	  * Restart the Computer

Having this type of functionality is really helpful from the perspective of a developer of services. Who wants to re-invent the wheel and have to write recovery code in the service if you can get it for free. Plus it allows the recovery to be reconfigured as an IT task as opposed to rebuilding the software.  I did discover a few gotchas along the way, though.  

**Building a Basic Service**
Let’s start with the basics though. You can create a service using Visual Studio by adding a project and selecting the type “Windows Service”. This will populate an empty service. First thing I like to do is give the classes and service real names. In this case I am testing that the recovery from a failure works so I renamed my class to FailingService.cs (not something I would recommend calling a product, but in this case it fits) . I also changed the ServiceName using the Properties of the window from Service1 (the default) to TestFailingService. This is the name that is going to appear in the Windows Services dialog, so I strongly recommend changing it.

You will also want to add an installer for your service as this will make it much easier to install the service onto your computer. You can’t run the service like a regular EXE file, so you definitely want an installer here.

Now that we’ve done all the basics, you should be able to build your service and install it. You can install the service using the InstallUtil.exe program that comes with the .NET Framework. Open a Visual Studio Command Prompt (this will already have a path to InstallUtil) and run

    
         InstallUtil ServicePath


Note: If there are spaces in the path you should enclose the path in “” as in InstallUtil "C:Documents and SettingsuserMy DocumentsVisual Studio 2005ProjectsServiceRecoveryTestsTestServicebinDebugTestService.exe"

Depending on how your PC is configured, you may be prompted to log in as part of installing the service.  If you are on a domain you should use the full user name of _domain__user_.

From the Services tab you should now be able to start and stop your service. You should also be able to go to the Windows Event Viewer and see events related to starting and stopping your service in the Application and System logs.

To uninstall the service use the commands above, but with the /u option, as in

    
         InstallUtil /u ServicePath


**Error Recovery**
What I really wanted to do was to work with the failure recovery features of the service, so the first thing I did was create a thread that would simulate an error on some background processing of the service. The thread sleeps for 30 seconds and then throws an exception.

Since this exception is being thrown on a different thread than the main thread, I need to subscribe to the AppDomain’s UnhandledException event. If I don’t do this the thread will just die silently and the service will continue to run, which is not what I want.

Initially I thought I could just take advantage of the ServiceBase class ExitCode property. I figured that if I set the ExitCode property to a non-zero value and stopped the service that would be interpreted as a failure and the service would automatically be restarted, as in

[sourcecode language='cpp']
        void UnhandledExceptionHandler(object sender, UnhandledExceptionEventArgs e)
        {
            ExitCode = 99;
            Stop();
        }
[/sourcecode]

That is not the case though as I found out [here](http://msdn2.microsoft.com/en-us/library/ms685939(VS.85).aspx). _“A service is considered failed when it terminates without reporting a status of SERVICE_STOPPED to the service controller.”_

So from this definition I decided that I needed to throw an exception in the Stop event handler, otherwise Stop would return normally, and it would not be considered a failure by the [SCM](http://en.wikipedia.org/wiki/Service_Control_Manager).What I finally ended up doing was having the unhandled exception handler cache the unhandled exception and call Stop. The Stop event handler then checks if there is an unhandled exception and wraps that in an exception and throws it. Wrapping the exception, and passing the asynchronous exception as the InnerException, preserves the call stack of the asynchronous exception.

**Examining the Event Viewer**
I configured the service to restart after the 1st and 2nd failures, but to take no action after the third.  The fail counters will reset after 1 day and the service will restart immediately after a failure.

[![Configuring Service Recovery 2](http://mdenomy.files.wordpress.com/2008/02/configuring-recovery-2.jpg)
](http://mdenomy.files.wordpress.com/2008/02/configuring-recovery-2.jpg)

The service is written to fail after 30 seconds and the recovery mechanism should restart it immediately.  If you start the log file you should see entries in the Event Viewer's Application or System log showing the service starting, failing, and restarting.

[![Viewing Service Events](http://mdenomy.files.wordpress.com/2008/02/viewingserviceevents.jpg)
](http://mdenomy.files.wordpress.com/2008/02/viewingserviceevents.jpg)

You can also get more information by opening up some of these events, such as service state transitions, how many times the error has occurred,  or detailed error messages.  Here is an example[![Examining Service Events](http://mdenomy.files.wordpress.com/2008/02/examiningservicecounters.jpg)
](http://mdenomy.files.wordpress.com/2008/02/examiningservicecounters.jpg)

**Resetting the Error Counters**
Unfortunately the _Reset fail count after_ and _Restart service after_ fields in the Recovery tab only takes integers.  It would have been nice to be able to have granularity less than a whole day for the reset of the counters to take effect.  If you are running this service repeatedly (like I was doing during testing) the counters may be too high to automatically restart the service.  If you expected a restart and didn't get one, examine the entries in the Event Viewer's System log and you should see something like this

If you want to reset the counters you can set the _Reset fail count after _field to zero which will cause the counters to reset after each failure.

**Turning Off the JIT Debugger**
One of the main reasons you write a service is to do something without user intervention (or even with a user logged in). One of the problems with this implementation is that you end up throwing an unhandled exception, by design, from the Stop event handler. If the Microsoft Just-In-Time (JIT) debugger is configured to run on your system it will prompt you if you want to debug the application. For a service that you want to auto-recover this is a really bad thing, since….well there might not be anyone there to answer the prompt.

I found a few tips on how to turn this off. You can read about them here.



	  * [How to: Enable/Disable Just-In-Time Debugging](http://msdn2.microsoft.com/en-us/library/k8kf6y2a(VS.80).aspx)
	  * [How to turn off/disable the .NET JIT Debugging Dialog](http://www.hanselman.com/blog/HowToTurnOffdisableTheNETJITDebuggingDialog.aspx)

Note: If you have multiple versions of Visual Studio installed (I have 2005 and 2003 installed) you have to turn off the JIT debugger for each version.

**Service Source Code**
Here is the source code for the service.  The service is designed to fail after 30 seconds to test the recovery mechanisms of the Windows services.  The code automatically generated for the installer was not modified at all, except to change the service name which was described above.

[sourcecode language='cpp']
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Diagnostics;
using System.ServiceProcess;
using System.Text;
using System.Threading;

namespace TestService
{
    public partial class FailingService : ServiceBase
    {
        private Thread _workerThread;

        // Used to cache any unhandled exception
        private Exception _asyncException;

        public FailingService()
        {
            InitializeComponent();

            // Wire up the UnhandledExcepetion event of the current AppDomain.  
            // This will fire any time an undandled exception is thrown
            AppDomain.CurrentDomain.UnhandledException += new UnhandledExceptionEventHandler(UnhandledExceptionHandler);
        }

        void UnhandledExceptionHandler(object sender, UnhandledExceptionEventArgs e)
        {
            // Cache the unhandled excpetion and begin a shutdown of the service
            _asyncException = e.ExceptionObject as Exception;
            Stop();
        }

        protected override void OnStart(string[] args)      
        {
            // Start up a thread that will simulate a failure by throwing an unhandled exception asynchronously
            _workerThread = new Thread(new ThreadStart(SimulateAsyncFailure));
            _workerThread.Start();

        }

        protected override void OnStop()
        {
            // If there was an unhandled exception, throw it here
            // Make sure to wrap the unhandled exception, as opposed to just rethrowing it, to preserve its StackTrace
            // To wrap it, create a new Exception and pass the unhandled exception as the InnerException
            // The exception info will be in the Windows Event Viewer's Application log
            // You could also use some logging/tracing mechanism to capture information about the exception 
            if( _asyncException != null )
                throw new InvalidOperationException("Unhandled exception in service", _asyncException );
        }

        private void SimulateAsyncFailure()
        {
            // Simulate an asynchronous unhandled excpetion by sleeping for some time and then throwing
            // There is no caller to catch this exception since it is running in a separate thread
            Thread.Sleep((int)TimeSpan.FromSeconds(30).TotalMilliseconds);
            throw new InvalidOperationException("Simulating a service error");
        }
    }
}
[/sourcecode]
**Programmatically Configuring Recovery**
The installers do not provide any support for programmatically setting up the recovery actions, which I find a little frustrating.  I did find some code [here](http://www.codeproject.com/KB/install/sercviceinstallerext.aspx) that will allow you to do this, but have not had a chance to test it out or incorporate it into the sample.
