---
author: mdenomy
date: 2010-04-15 15:31:54+00:00
draft: false
title: R&D IT Best Practices for Growing Small/Mid-Sized Biopharmas
type: post
url: /2010/04/15/rd-it-best-practices-for-growing-smallmid-sized-biopharmas/
tags:
- Cloud Computing
---

The [Mass Technology Leadership Council](http://www.masstlc.org/) put on a round table discussion on best practices for small/mid sized biopharmas at Microsoft NERD on April 14.  The agenda is shown below

<blockquote>As smaller biopharma companies grow and mature into larger organizations, they need to transition from relatively ad hoc, spreadsheet heavy, lightly supported R&D IT environments to more comprehensive, scalable platforms and support models. This presents substantial challenges to scientists, managers, and IT professionals, ranging from prioritization of new features and functions, creation of new workflows, budget and staffing issues, in-house platforms versus COTS (commercial-off-the-shelf) platforms, and getting support for necessary changes. Our expert panel will discuss these issues and more in this MA Technology Leadership Council Life Science Cluster roundtable discussion.</blockquote>

The discussion covered a range of topics from virtualization of IT, data management, build vs. buy, and collaborating with scientists.

**Virtualization and Cloud Computing**

Cloud computing is a very hot topic these days and there is obviously a lot of interest in this area for small and mid-sized biopharmas.  Being able to pay-as-you go has a lot of appeal and the reduced infrastructure costs are appealing.  Being comfortable with having your hardware, software, and especially your data outside of your direct control is still an issue for a lot of people.  Regulatory issues like [HIPAA](http://www.hhs.gov/ocr/privacy/hipaa/administrative/index.html) and protecting your intellectual property are still concerns for people.  Uploading large data sets, on the order of gigabytes, is still not a workable solution and it is often [easier and cheaper to ship the data sets to be uploaded](http://searchcloudcomputing.techtarget.com/news/article/0,289142,sid201_gci1357086,00.html).

There was a lot of discussion about security of data and whether you are more secure having your data hosted by some organization that (hopefully) has significant resources dedicated to security or are you more at risk with having data in house.  A lot of data and IP leaves most companies every day in the form of laptops, USB sticks, email attachments, etc, which presents its own set of security concerns.

**Collaborating With Scientists**

There was a very good discussion about how to collaborate with the scientists to build tools to manage data.  The take-away from this discussion was to understand their work flow and to learn what the do instead of just asking what they need.  By understanding their workflow you are in a better position to understand their needs.  One of the panelists made an interesting comment that scientists tend to feel that what they do is unique, and that is why there may be some resistance to a commercial-off-the-shelf (COTS) solution.  They also tend to shut down when given a complete solution, and are much more receptive to being part of the process of defining the solution.

As a practitioner of [Agile](http://agilemanifesto.org/), this makes perfect sense to me.  You can't deliver a solution to your end users if you don't understand their workflow and they are an integral part of defining the solution.  Also by building solutions incrementally, you allow for refinement and early feedback from your end-users.

**Data Management Policies**

One of the themes that all the panelists touched on was trying to deal with data being spread across the company in a variety of formats.  When a company is in its early stages, lots of "data" resides in spreadsheets and PowerPoint presentations, and most people know where it is or can give you enough clues to find it, e.g. "Bob did a presentation back in May that....".

As companies grow this data becomes harder and harder to manage.   Content management tools like [SharePoint ](http://sharepoint.microsoft.com/Pages/Default.aspx)and [Documentum](http://www.emc.com/products/category/subcategory/documentum-platform.htm), or [LIMS](http://en.wikipedia.org/wiki/Laboratory_information_management_system) systems can address issues like these, but there are setup and maintenance costs that can be an issue for a small start-up.

Probably the biggest takeaway for me from the entire session was the notion of putting a data management strategy in place early on.  The strategy would address issues like where/how to store data.  A policy would not need to be restrictive, just some basic rules.  That way when the need to add tools and support to manage the data arises, incorporating the data into the system will be easier.

Coming at it from an [Agile](http://agilemanifesto.org/principles.html) perspective, this makes a lot of sense.  Do the simplest thing, i.e. a basic policy of how to store your data, before going to a heavyweight approach of a full blown LIMS or content management system.  The key here would seem to be to make sure the policy is easy to understand and implement and is not a barrier to innovation.  The last thing you want is people NOT using the policy because it is an impediment to progress.  Coming back to the idea of collaboration and understanding your user's workflow, you want to make your user part of defining the policy.

**Build vs Buy
**

Build versus buy needs to be balanced by the start-up costs and learning curve of using COTS solution versus the long term costs of maintaining custom solutions.

As time goes on, the maintenance costs for custom solutions can become prohibitive, especially as the amount of data (and required features) grows and/or the principles who developed the tools move on.

Open source tools have a lot of appeal as they offer some level of off-the-shelf capabilities and community support with the ability to customize if needed.  People in the bioinformatics space are often not comfortable with proprietary algorithms/solutions and want to be able to see what's under the covers.

**Other Interesting Nuggets**

Other interesting things that came up are...

Periodic technical audits of your tools, processes, etc.  Having someone from the outside come in and take a look at how you are doing things.  Are you behind the curve, have you become numb to certain pain points that can be fixed.  Finding someone to do this who you trust and doesn't have a vested interest in selling you a particular solution may be a challenge, but I found this to be an intriguing idea.

What sample tracking systems are available that manage secondary samples.  For example if you do extractions or build a library from a base sample, how do you trace that relationship back to the parent sample.

As companies move towards a regulated space, tools that provide an audit trail are very appealing to IT groups.

In summary it was an interesting discussion and gave me a lot to think about.
