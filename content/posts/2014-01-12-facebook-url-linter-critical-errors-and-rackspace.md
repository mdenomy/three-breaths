---
author: mdenomy
date: 2014-01-12 14:24:41+00:00
draft: false
title: Facebook URL Linter, Critical Errors, and Rackspace
url: /2014/01/12/facebook-url-linter-critical-errors-and-rackspace/
tags:
- Social Media
- Facebook
- OpenGraph
- Rackspace
---

When you share a URL on Facebook, Facebook will scrape the page to find the [Open Graph data](https://developers.facebook.com/docs/web/tutorials/scrumptious/open-graph-object/) embedded in the page.

Facebook also provides a tool called the [Open Graph Object Debugger](https://developers.facebook.com/tools/debug/) to help you debug errors found in the page.  This can be rally useful if, for instance, your tags are not well-formed, or there are problems with the images or videos that are on the page being shared.

Sometimes, unfortunately, you get a dreaded "Critical Errors That Must Be Fixed - Error Linting URL" as shown below.

[![UrlLinterCriticalError](http://mdenomy.files.wordpress.com/2014/01/urllintercriticalerror.png)
](http://mdenomy.files.wordpress.com/2014/01/urllintercriticalerror.png)

Unfortunately, this doesn't tell you a lot about the cause of the error.  I was trying to have an image display using the [og:image tag](http://ogp.me/).  I had been able to successful share pages that had images that were in my Rails  asset directory, but this particular page used an image that was hosted on [Rackspace Cloud Files](http://www.rackspace.com/cloud/files/).

To try and diagnose whether there was a problem with the image (e.g. corrupt file, invalid size for Facebook, etc) I downloaded the image and stored it in my Rails assets.  Everything worked fine.  No errors from the Facebook URL Linter.  The problem must have something to do with the storage on Rackspace.  But browsing to the image on Rackspace worked fine as well.  The image displayed fine in the browser and was publicly accessible.

Why wasn't the Facebook URL Linter able to parse it?
Well when you store files with Rackspace Cloud Files, you get a pretty hideous URL, like

    
    http://12345678901234567890-12345678901234567890123456789012.r12.cf3.rackcdn.com


A URL is a URL right?  Well yes and no.  I think the Facebook URL Linter finds this to be a pretty suspect URL and considers it spammy.  So I needed to make the URL a little more "friendly" to a spam filter.

The answer was to use a [CNAME](https://support.google.com/a/answer/112037?hl=en) to [map a more readable URL to the Rackspace URL](http://www.rackspace.com/blog/its-here-cloud-files-now-supports-cnames-for-cdn-enabled-content/).

My client's site is hosted on GoDaddy, so that meant going into their DNS settings and adding a CNAME record to point to the Rackspace URL.  I picked something meaningful like "images".  So now my og:image tag could change from

    
    <meta property="og:image" content="http://12345678901234567890-12345678901234567890123456789012.r12.cf3.rackcdn.com/some_image.png">


to

    
    <meta property="og:image" content="http://images.mydomain.com/some_image.png">


In hindsight, the CNAME is a good idea on its own. Sure it might be an extra hop to get the image, but having a more logical URL makes a lot of sense, and it also makes in easier to change where your images are stored.
