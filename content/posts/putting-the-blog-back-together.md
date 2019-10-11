---
title: "We're Putting The Blog Back Together"
date: 2019-10-10T08:29:47-04:00
draft: false
---

Wow, has it really been 4 years since I've blogged? Well, I've got some good news.

<iframe src="https://giphy.com/embed/U6YiNxZEQjSoIGK8jj" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/U6YiNxZEQjSoIGK8jj"></a></p>

I started my blog on <a href="https://wordpress.com/" target="_blank">Wordpress</a>. There's nothing wrong with Wordpress, really. It let me easily generate content, and, at the time, my background in software was geared more toward laboratory automation, robotics, and medical device development. I was not a web developer. 

But I always felt a little...dirty, for lack of a better word, about having my blog on Wordpress. It seems like a software engineer should be a bit more intentional about the tools they use.

Well after years of procrastinaton, I finally got around to moving my blog off of Wordpress. I hope this leads to a renewed interest in blogging, especially in some of the more managerial topics that excite me these days.

For those who are curious, this is how I went about porting my blog.

## Picking the Tools

### Site Generation

I just wanted a simply site for a blog, so a static site generator seemed to be the way to go. New tools and frameworks are always coming out, but the two primary tools I considered were [Hugo](https://gohugo.io/) and [Jeckyll](https://jekyllrb.com/). Both have a lot of traction in the community and both seemed easy to get started.

I'm [Go](https://golang.org/)-curious, and though you don't need to know any Go to get up and running, I thought maybe using Hugo would be a bit of a gateway drug to Go. Also, though Jeckyll looks very feature-rich, Hugo struck me as a little leaner, with great [docs](https://gohugo.io/documentation/). So after trying out the Hugo [Quick Start](https://gohugo.io/getting-started/quick-start/), I decided to give it a go (no pun intended).

I wanted a lean, clean style, so I went with the [ezhil](https://github.com/vividvilla/ezhil) theme.

### Porting My Past Content
It was surprising to see that I started blogging in 2007. I'm not a prolific blogger, but it was a lot of fun to see how far the content went back, and I think it is all part of my story. I didn't want to lose it.

It seems like some of the tools for porting Wordpress to other platforms maybe slightly favored Jeckyll, but I was able to [port the content for Hugo](https://gohugo.io/tools/migrations/).

After a few false starts with [wordpress-to-hugo-exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter), I ended up having success with [exitwp-for-hugo](https://github.com/wooni005/exitwp-for-hugo), which was just a simple python script that converted the exported XML file from Wordpress to a bunch of markdown files. That was good enough.

I had to do a little cleanup, fixing video embeds (Hugo's [shortcodes](https://gohugo.io/content-management/shortcodes/) were really helpful here, especially for youtube and tweets). I needed to add some iframes to embed keynotes and slides from [Slideshare](https://www.slideshare.net/). Code blocks had to be converted to standard Markdown format, but really, that was so much easier than managing code blocks in Wordpress.

I still have some media, mostly JPGs, that I need to port, but they work right now. A chore for another day

### Hosting

This is another area where I felt the Hugo [docs](https://gohugo.io/hosting-and-deployment/) shined. After reviewing the docs, I felt like one of two options would work best for me.

* [Host on Github Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
* [Host on Netlify](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)

I felt like GitHub Pages would have worked for me, but in some ways it felt a little too easy and besides, when am I gonna get to use the custom domains I've purchased.

Netlify looked like a clean, easy to use solution, that was also free for my needs. Though there wasn't a lot of setup, it was fun to confige DNS. Netlify's docs on this were excellent, and it was pretty simple to set up a CNAME and and ALIAS to work with my [DNSimple](https://dnsimple.com). Netlify made it really simple to set up HTTPS too.

## Next Steps

So what remains now is to start writing. There are some recent twitter rants that I think will make some good posts.

Stay tuned.