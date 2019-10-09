---
author: mdenomy
date: 2009-01-23 00:37:09+00:00
draft: false
title: Head in the Cloud with Windows Azure
type: post
url: /2009/01/22/head-in-the-cloud-with-windows-azure/
tags:
- .NET
- Cloud Computing
- Software
- Visual Studio
---

Microsoft hosted a [developer conference](http://msdndevcon.com/Pages/Boston.aspx) in Boston today.  I think for the most part, you get when you pay for, and the $99 price of this event told me it would probably be more marketing than technology.  But it's always good to get out and hear what's going on and talk with other developers.

There were several topics of interest to me at the conference, ranging from [F#](http://msdn.microsoft.com/en-us/fsharp/default.aspx), [Silverlight](http://silverlight.net/), [Visual Studio Team System 2010](http://www.microsoft.com/Visualstudio/products/2010/default.mspx), and [ASP.NET 4.0 ](http://www.pluralsight.com/community/blogs/fritz/archive/2009/01/21/demos-for-asp-net-4-0-roadmap-talk-msdn-developer-conference-nyc.aspx), but one of the things I was most interested in learning about is [Azure](http://www.microsoft.com/azure/default.mspx), Microsoft's foray into [cloud computing](http://en.wikipedia.org/wiki/Cloud_computing).  I thought that this conference would give me a good 50,000 foot view into Microsoft's plans for a cloud computing paltform.

In the keynote, [Amanda Silver](http://msdn.microsoft.com/en-us/vbasic/bb735849.aspx#silver) referenced [the Battle of the Currents](http://en.wikipedia.org/wiki/War_of_Currents), where in the early days of electrical distribution Thomas Edison's system of direct current (DC) was pitted against Nikola Tesla and George Westinghouse's system of alternating current (AC).  One of the disadvantages of direct current was that the power generation had to be close by due to power loss associated with transmission.  This meant that a manufacturing plant might need to have its own electrical plant, with all the associated capital costs and maintenance. This is much the same as technology companies today incurring the capital cost and IT support of maintaining their own data centers.  The ability to buy electric power from a utility company would allow the consumer to focus on their business and treat the incoming power as a service.

Microsoft's intention in this market seems to be to offer a similar utility model that would have the benefits of scalability, redundancy, and IT support and allow a company that subscribes to the Microsoft data center services to focus on it's own business domain.  As any of us who have had internal data centers know, power outages, scaling, and IT support (security patches, etc.) can be a real headache for a developer and data center IT support keeps us from doing our real jobs: design and writing code.

Now before you think I [drank too much Microsoft Kool-Aid](http://www.wordspy.com/words/drinktheKool-Aid.asp), I am just saying that is the idea behind cloud computing in general.  Why absorb the capital outlay and support costs of setting up and maintaining a data center when you can lease those capabilities?  Theoretically, this could lead to better support, scalability, and fault tolerance.  Microsoft seems to be positioning itself for proving data center services and support in the future.  How far off in the future is a question that remains to be answered.

The presentations on Windows Azure presented a fairly realistic picture of where the technology is today, and I give the presenters credit for that.  [Michael Stiefel's ](http://www.reliablesoftware.com/DasBlog/default.aspx)presentation was good and gave the 50,000 foot view that I was looking for.  He also drilled down a little bit into the services provided in Azure, including  high level.  [Ben Day's presentation](http://blog.benday.com/archive/2009/01/23/23211.aspx) was particularly good I thought, pointing out the potential of the technology while balancing that against some of the limitations of the current implementation, particularly related to Azure data storage.  I would assume their blogs will have the presentations at some point in the future, so you may want to check in.

The presentations and keynote showed how you can get started with Azure today using Visual Studio 2008.  You will need to install the Azure SDK and Azure Tools for Visual Studio that you can find [here](http://www.microsoft.com/azure/sdk.mspx). Azure applications can execute locally on a [Development Fabric](http://msdn.microsoft.com/en-us/library/dd203061.aspx), which is a simulated cloud environment on your desktop. You can also deploy a service to run in the Azure cloud, but you need to [set up an account](http://www.microsoft.com/azure/register.mspx) for that, and for the purposes of learning about the technology it would seem that the Development Fabric is adequate.  The developer "experience" (another big buzzword at the conference) is the same as developing other Windows apps in Visual Studio.  You can debug applications normally if they are running in the Development Fabric, however once they are deployed the only debug mechanism is logging statements.

This is definitely a "down the road" technology, and there are several kinks to work out, but if you want to be ahead of the curve it might not be a bad idea to try some of it out.  One of the things that came up in the presentations is that Microsoft is on the fence on some aspects of the implementation and will be looking to the developer community for feedback.  We'll have to wait and see how all this plays out, but I am certainly willing to give it a spin.
