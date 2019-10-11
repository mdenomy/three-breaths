---
author: mdenomy
date: 2014-02-13 02:01:51+00:00
draft: false
title: 'Responsive Design Comparison: Neat vs Foundation'
url: /2014/02/12/responsive-design-comparison-neat-vs-foundation/
tags:
- CSS
- SASS
- Styling
---

In the interest of improving my design skills, I wanted to brush up on a couple of different grid-based systems that provide responsive design capabilities.  There are several to choose from, but I settled on trying out [thoughtbot's neat](http://neat.bourbon.io/) library and [Zurb's Foundation](http://foundation.zurb.com/) framework.  Along the way, I also got a chance to play around with [thoughtbot's Bourbon](http://bourbon.io/) library.


## Just The Grid, Thanks


Now first off, comparing neat to Foundation is like comparing apples to fruit salad.  neat is strictly a grid system, it is not a full-blown framework, like Foundation.  There is a time and a place for either approach, but since I wanted to focus primarily on how the two grid systems work I think it is mostly a fair comparison.

I developed two bare-bones apps that just let me play around with the grid system and some basic styling.  All I really wanted to do with the apps was to have a few static pages, see how the grid system layout worked, and how it responded to different screen sizes (desktop, tablet, phone).  The apps can be found here.

  * [https://github.com/mdenomy/neat-demo](https://github.com/mdenomy/neat-demo)
  * [https://github.com/mdenomy/foundation-demo](https://github.com/mdenomy/foundation-demo)

These apps are a simulation for a wine store application.  Again, wasn't going for a full functioning app.  Just wanted the following features in the demo apps

  * Page header with some simple navigation links
  * Home page with a grid-based sections for "Staff picks" and "Calendar of events"
  * Responsive design to change the layout for desktop/laptop, tablet, and phone contexts

## tl;dr

Either neat or Foundation is a solid choice for a grid system.  Both default to 12-column grids, and can configured to support other layouts.  Both are really easy to integrate into a Rails application.  Both also have good documentation, though I might give Foundation a slight nod there.

As far as just the grid system, my preference would be for Foundation.  For me, the syntax of defining the grid system seemed a little more straightforward.  I also liked that when nesting, the child elements don't need to know about the number of columns in the parent.

Going with a full framework also brings some extra functionality.  I was able to play around with the [block grid](http://foundation.zurb.com/docs/components/block_grid.html), the [top-bar navigation](http://foundation.zurb.com/docs/components/topbar.html), and the easy to set up "hamburger" menu icon.  I think it has really solid documentation as well.

Now let's get to the details...

## neat


neat defaults to a 12-column grid, which I like a lot since your sections can easily switch between multiples of 3 or 4 without changing the overall number of grids.  You have the ability to configure the number of columns you want the grid to have, but I had no reason to want to do that with what I was doing.

A grid region is defines using the [outer-container](http://neat.bourbon.io/docs/#outer-container) mix-in.  According to the neat docs, you can have multiple outer-containers on a page, however they can not be nested.  Given the simplicity of my app, I just threw it on the body element.

``` html
    body {
      background-color: $background;
      color: $text;
      font-family: 'lato';
      @include outer-container;
    }
```

The [span-columns](http://neat.bourbon.io/docs/#span-columns) mix-in is used to specify how many columns an element should span.  If the element is nested, you must also specify the number of columns its parent element contains, for example, **@include span-columns(4 of 8)** specifies that the element takes up 4 columns of an 8 column parent.  I personally found having to specify the parent information to be a bit of a nuisance, and one where neat and Foundation differed.  It wasn't a show-stopper, but I didn't like having to concern myself with it.

Responsiveness is attained using the [media](http://neat.bourbon.io/docs/#media) mix-in.  Inside of the block for the media mix-in, you can define the features for that context.  This allows you to redefine columns, font sizes, whatever for that particular context, e.g. tablet or mobile.  This gives you a lot of control, but to me felt a little heavy. Here you can see where I define that an element normally spans 4 of 8 columns, but for the tablet and mobile contexts spans 4 of 4 columns.

``` css
    .staff-pick {
      @extend .tile;
      @include span-columns(4 of 8);
      @include omega(2n);
      @include media($tablet) {
        @include span-columns(4 of 4);
        @include omega();
      }
      @include media($mobile) {
        @include span-columns(4 of 4);
        @include omega();
      }
    ...
    }

```

You can also change the width for when the context switches as well as the number of columns in the grid for the context using the [new-breakpoint](http://neat.bourbon.io/docs/#new-breakpoint) mix-in.  For my application, I went with an 8 column tablet breakpoint and a 4 column mobile breakpoint.

    
    $tablet: new-breakpoint(max-width 900px 8);
    $mobile: new-breakpoint(max-width 600px 4);


I think one of the strengths of neat may be that you have very fine-grained control or the grid and underlying elements through the [multiple mix-ins it provide](http://neat.bourbon.io/docs/)s, but that will also take a little more work (or familiarity on neat) on your part.  I also found it required reading both the [gem docs on github](https://github.com/thoughtbot/neat) and the [neat page docs](http://neat.bourbon.io/docs/) to fully understand how to set it up and get running.


## Foundation


As I said earlier, [Foundation](http://foundation.zurb.com/) is a full blown framework, along the same lines as [Twitter Bootstrap](http://getbootstrap.com/).  You get the grid system, but also navigation elements, buttons, forms, controls of all different kinds, alerts, drop-downs, and on and on.  But for the purposes of this comparison, I wanted to concentrate primarily on the grid system.

Like neat, Foundation uses a 12-column grid, and like I said earlier, a 12-column grid has a lot of advantages.  You can also customize the number of columns in the grid system, but the default was fine for what I was doing.

Foundation uses a different format for specifying the grid layout.  Rather than try and spell it out in all it's detail, take a look at the [grid documentation](http://foundation.zurb.com/docs/components/grid.html).  Overall, I found the ability to specify the columns all on one line more readable than the way neat does it.

To define an element that spans 4 columns for large screens and 2 for mobile, you would do something like this

    
    <div class="row"> 
      <div class="small-2 large-4 columns">...</div>
      ...
    </div>


Whereas with neat, you would do it this way

    
      .some-style {
        @include span-columns(4);
        @include media($mobile) {
          @include span-columns(2);
        }
      }


Foundation also has some nice features that make layout a lot easier, IMO.  My toy app had a section for "Staff Picks" that displayed a bunch of wines in a grid layout.  With Foundation, I could use the [Block Grid](http://foundation.zurb.com/docs/components/block_grid.html) feature to easily lay out the grid based on the screen size.

``` html  
    <div class="row">
      <ul class="small-block-grid-1 medium-block-grid-1 large-block-grid-2">
        <% @reviews.each do |review| %>
           .......
        <% end %>
      </ul>
    </div>
```

Now in 1 line, I can easily see that the block-grid will have

  * 1 review per row for a small screen
  * 1 review per row for medium screen
  * 2 reviews per row for large screen

Foundation also provides some easy mechanisms to implement a "hamburger menu" (the three vertical bars) for the navigation links when going to a small screen, using the **class="toggle-topbar menu-icon"** line.

``` html   
    <nav class="top-bar" data-topbar>
      <ul class="title-area">
        <li class="name">
          <h1><%= link_to "Denomy's Wine Emporium", root_path %></a></h1>
        </li>
        <li class="toggle-topbar menu-icon"><a href="#"></a></li>
      </ul>
      <section class="top-bar-section">
        <ul class="right">
          <li><%= link_to 'Home', root_path %></li>
          <li><%= link_to 'About', about_path %></li>
          <li><%= link_to 'Help', help_path %></li>
        </ul>
      </section>
    </nav>
```

Foundation also provides a lot of tools for handling nesting, offsets, incomplete rows, and other potential gotchas that really look great for helping to manage the grid.

Given that you get a lot of other features with it, like forms, alerts, drop-downs, etc, I am really starting to look forward to using Foundation more in the future.

It wasn't all perfect, there were some annoying things.  For instance, I was unable to use a linear gradient in the header bar, but for the most part it was pretty easy to work with.

## Adding In a Splash of Bourbon

I am happy to say that it was easy to use both neat and Foundation in a Rails app with Bourbon.  Bourbon has some a really rich set of SASS mixins that can be used to customize the look of your app.
