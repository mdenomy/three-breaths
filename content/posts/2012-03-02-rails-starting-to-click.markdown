---
author: mdenomy
date: 2012-03-02 13:57:00+00:00
draft: false
title: Season of Ruby - Things Are Starting To Click
url: /2012/03/02/rails-starting-to-click/
tags:
- Rails
- Season of Ruby
- TDD
---

The danger with doing any online tutorial, even one as good as the [Michael Hartl Rails Tutorial](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book), is that if you aren't careful the only benefits you will have at the end is that your typing skills have improved and you have the marketable ability to cut-and-paste large snippets of code.  At some point you need to start driving the bus.  Today I felt like the [Ralph Kramden](http://en.wikipedia.org/wiki/The_Honeymooners#Ralph_Kramden) of Rails.

[![](http://mdenomy.files.wordpress.com/2012/03/honeymooners2.jpg?w=300)
](http://mdenomy.files.wordpress.com/2012/03/honeymooners2.jpg)

_Editor's Note: I am not actually old enough to have seen the Honeymooner's, I just remember in my college days the reruns were on at 11PM, just before Star Trek at midnight (also in reruns)._

The last few chapters I have been making an effort to implement the code without looking at the solution from the tutorial.  Today I stepped it up a little further by taking more control of writing and defining the tests too.  It really paid off today as I felt like I took ownership of the app and the technical choices.

[Chapter 10](http://ruby.railstutorial.org/chapters/updating-showing-and-deleting-users#top) starts out by defining the functionality needed for editing a user.  I looked over the [wireframes](http://ruby.railstutorial.org/chapters/updating-showing-and-deleting-users#sec:edit_form) and had a good idea about the functionality I wanted.  I glanced at the titles of the [1st three tests](http://ruby.railstutorial.org/chapters/updating-showing-and-deleting-users#code:user_edit_specs): get page successfully, has correct title, and includes link to change gravatar.

From a pure TDD approach, [doing the simplest thing that work](http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html)s, I was able to get these tests to pass with the following code.

**app/views/users/edit.html.erb**

``` ruby
<h1>Edit User</h1>
<a href="http://gravatar.com/emails">change</a>
```


**app/controllers/user_controllers.rb**


``` ruby
 class UsersController < ApplicationController
    ...
    def edit
      @title = "Edit user"
    end
    ...
```

Obviously this is not enough to implement the final solution, but it _**is enough**_ to get the tests to pass, and in my experience additional functionality should be driven by the tests.  From the perspective of a Rails noob I felt that these were valuable tests because they proved out the plumbing and set the table for more complex tests/functionality.  Now it was time to look at the tutorial's [solution](http://ruby.railstutorial.org/chapters/updating-showing-and-deleting-users#code:initial_edit_action).

I was surprised to see that the tutorial solution included the form and all its associated fields.  Now this is not a knock on the tutorial, it is a very good tutorial.  I love this tutorial, but while it introduces some concepts of TDD and its primary goal is not to teach TDD.  But clearly there was a disconnect between the solution and the tests.

So I added the tests for the fields, and now was happily back to red.  Yes Virginia, real developer's love failing tests, they are a sign of progress.

**spec/controllers/user_controllers_spec.rb**

``` ruby
   it "should have a name field" do
      get :edit, :id => @user
      response.should have_selector("input[name='user[name]'][type='text']")
    end

    it "should have an email field" do
      get :edit, :id => @user
      response.should have_selector("input[name='user[email]'][type='text']")
    end

    it "should have an password field" do
      get :edit, :id => @user
      response.should have_selector("input[name='user[password]'][type='password']")
    end

    it "should have an confirmation field" do
      get :edit, :id => @user
      response.should have_selector("input[name='user[password_confirmation]'][type='password']")
    end
```

Getting to green was fairly trivial, and I was able to cut-and-paste a lot of the code from "new" and make a few minor mods.

**app/views/users/edit.html.erb**

``` ruby
<h1>Edit User</h1>
<%= form_for(@user) do |f| %>
  <%= render 'shared/error_messages', :object => f.object %>
  <div>
    <%= f.label :name %><br />
    <%= f.text_field :name %>
  </div>
  <div>
    <%= f.label :email %><br />
    <%= f.text_field :email %>
  </div>
  <div>
    <%= f.label :password %><br />
    <%= f.password_field :password %>
  </div>
  <div>
    <%= f.label :password_confirmation, "Confirmation" %><br />
    <%= f.password_field :password_confirmation %>
  </div>
<div>
  <%= f.submit "Update" %>
</div>
<% end %>
<div>
  <a href="http://gravatar.com/emails">change</a>
</div>
```

My tests were passing but now I had quite a bit of duplicated code in my app/views/users/new.html.erb and app/views/users/edit.html.erb files.  It was time for the 3rd piece of the red-green-refactor cycle.

Thinking back to earlier chapters, I thought what I would like to do is to implement a partial view that encapsulated the user forms.  After some googling about how to[ pass parameters into a partial view](http://stackoverflow.com/questions/6672454/passing-parameters-to-partial-view) I ended up with the following partial view

**app/views/shared/_user_fields.html.erb**

``` ruby
<div class="field">
  <%= f.label :name %><br />
  <%= f.text_field :name %>
</div>
<div class="field">
 <%= f.label :email %><br />
 <%= f.text_field :email %>
</div>
<div class="field">
 <%= f.label :password %><br />
 <%= f.password_field :password %>
</div>
<div class="field">
 <%= f.label :password_confirmation, "Confirmation" %><br />
 <%= f.password_field :password_confirmation %>
</div>
```
And the edit.html.erb was a lot cleaner now and my tests were still passing.
**app/views/user/edit.html.erb**


``` ruby
<h1>Edit User</h1>

<%= form_for(@user) do |f| %>
 <%= render 'shared/error_messages', :object => f.object %>
 <%= render 'shared/user_fields', :f => f %>
 <div class="actions">
 <%= f.submit "Update" %>
 </div>
<% end %>

<div>
 <a href="http://gravatar.com/emails">change</a>
</div>
<pre>
```

Making the necessary changes to new.html.erb completed the process.

**app/views/user/new.html.erb**

``` ruby
<h1>Sign up</h1>
<%= form_for(@user) do |f| %>
  <%= render 'shared/error_messages' %>
  <%= render 'shared/user_fields', :f => f %>
  <div class="actions">
    <%= f.submit "Sign up" %>
  </div>
<% end %>
```

Run the tests one more time...and still green.

It was a really good day in Rails land.  None of this was rocket-science, but I felt like I knew what I wanted to do and how to do it (with just a few minor hiccups related to syntax and mechanics).
