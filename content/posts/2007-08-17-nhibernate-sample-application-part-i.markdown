---
author: mdenomy
date: 2007-08-17 16:55:42+00:00
draft: false
title: NHibernate Sample Application - Part I
type: post
url: /2007/08/17/nhibernate-sample-application-part-i/
tags:
- NHibernate
- Software
---

I was telling a friend about my NHibernate Skunk Works project.  He asked if I had an application in mind and I said I was planning on doing a wine inventory/tasting notes application and that I would start on the database this weekend.  His response stopped me right in my tracks "Why don't you write a scenario, first".  He's right, I got so focused on the technology that I stepped right over defining what I expected out of the application.   Just because it's a skunk works project doesn't mean I shouldn't be following good developer practices.  Here is a very brief description of the intended user (the persona) and an initial implementation scenario.

**Persona - Mark Atwood**
Mark Atwood recently began collecting wine as a hobby.  Mark has a collection of around 100 bottles, and enjoys pairing wines and foods.  Mark and his wife Beth often invite friends over to try wines and compare tasting impressions.

**Scenario - Wine Inventory and Tasting Notes Database**
Mark currently relies on memory for wines that he has enjoyed and what foods paired well with them.  As his collection has grown it has become harder to track that information.  Mark would like a system that allows him to keep track of his current wine inventory as well as a way to store and retrieve tasting notes.  Initially this application will run as a simple Windows Forms application.  The implementation should allow for eventual migration to a web-based application to allow the system to be used by multiple users

Mark would like to track the following information regarding a purchase of wine.



	  * Name
	  * Region
	  * Price
	  * Where/when it was purchased
	  * Grape variety - Note a particular wine may be a blend of different grapes

The application will allow a user to enter a wine purchase, prompting for the number of bottles purchased and the information stored above.  The data will be persisted in a database.

The application will allow a user to indicate that a bottle of wine has been opened.  The user will select a wine from the inventory and record the open date.  The date will default to the current date.

Mark would also like to track tasting notes for a particular opened bottle of wine.  The application will display opened bottles of wine, ordered by most recently opened bottle first.  The user will select a bottle and be able to enter the following tasting notes.

	  * Taster
	  * Tasting date
	  * Tasting notes

NOTE: For this scenario, food pairing information will be maintained in the body of the tasting notes.  In the future, the database may be extended to include more detailed food pairing information
