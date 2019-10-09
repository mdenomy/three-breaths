---
author: mdenomy
date: 2014-08-29 13:25:47+00:00
draft: false
title: Previewing emails in Rails applications with the mail_view gem
type: post
url: /2014/08/29/previewing-emails-in-rails-applications-with-the-mail_view-gem/
tags:
- Rails
---

Mailer specs are a great to verify that the emails sent from your Rails applications have the required data, links, and important content.  But often a developer, or more likely the product owner, may want to see the emails to make sure they are properly formatted, read well, and are free of spelling errors.

Getting your application to send an email from a development or staging environment can be an onerous task depending on how much user workflow and data setup is required for a given email.  This is where the [mail_view](https://github.com/basecamp/mail_view) gem can really help you out.

The [mail_view](https://github.com/basecamp/mail_view) gem lets us easily preview emails right from within your Rails application running in the development environment



## Using mail_view in Rails 4.1+





### Configuring mail_view



[mail_view](https://github.com/basecamp/mail_view) is built into Rails 4.1+, so there is no additional setup or configuration to start using it.

You can read more about support for mail_view in Rails 4.1 in the following links

[Edge Guides Release Notes](http://edgeguides.rubyonrails.org/4_1_release_notes.html#action-mailer-previews)

[ActionMailer API Docs](http://api.rubyonrails.org/v4.1.0/classes/ActionMailer/Base.html#class-ActionMailer::Base-label-Previewing+emails)



### Setting up emails to preview



By default, Rails 4.1 expects the mail preview classes to be located in the test/mailers/previews directory.  If you use the mail generator, a preview file will be created for you automatically. You create a class that inherits from ActionMailer::Preview for each email to be previewed.

[code lang=text]
class WelcomeMailerPreview < ActionMailer::Preview

  def welcome_investor
    user = User.last
    WelcomeMailer.welcome_investor(user)
  end

end
[/code]



### Previewing the emails



Browsing to http://localhost:3000/rails/mailers/welcome_mailer/welcome_investor will show you a preview of the email.  But before you do that you will probably need to set up some data for the preview



## Using mail_view in Rails prior to 4.1





### Configuring mail_view



For Rails versions prior to 4.1, there is just a little work to do to get set up.

First you will need to add the gem to your Gemfile.

[code lang=text]
gem "mail_view", "~> 2.0.4"
[/code]

Then you mount the mail_view engine into your application via the routes.rb file.

[code lang=text]
  if Rails.env.development?
    mount MailPreview => 'mail_view'
  end
[/code]

I wanted to make the mail_view available on my staging server, so I used an environment variable to enable it.

[code lang=text]
  if Rails.env.development? || ENV["PREVIEW_EMAIL"] == "true"
    mount MailPreview => 'mail_view'
  end
[/code]

With the engine mounted at mail_view, browsing to [http://localhost:3000/mail_view](https://s3.amazonaws.com/mail_preview_blog/MailPreviewList.png) will present us with a list of emails to preview.  But before we do that, we need to set up the emails to preview.



### Setting up emails to preview



You set up the emails to preview by creating a class that inherits from MailView

[code lang=text]
class MailPreview < MailView

  def welcome
    user = User.last
    WelcomeMailer.welcome_investor(user)
  end

  def payment_confirmation
    payment = Payment.last
    PaymentConfirmationMailer.confirmation_email(payment)
  end

  def contact_us
    ContactMailer.contact_email("Joe Smith", "617-555-1212", "jsmith@example.com", "I have a question...")
  end
[/code]



### Listing the emails



Now that we have some emails to preview, we can browse to [http://localhost:3000/mail_view](https://s3.amazonaws.com/mail_preview_blog/MailPreviewList.png) will present us with a list of email preview links as defined in the MailPreview class.
![Mail Preview List](https://s3.amazonaws.com/mail_preview_blog/MailPreviewList.png)




## Providing data for the emails



Typically our emails are working with data from our database.  The mail_view [documentation](https://github.com/basecamp/mail_view#usage) describes some of the ways you can provide data to the mailer, using either actual data from the database, using a factory pattern, or providing a stub.

In the examples above, I am using data from the database.  Each approach has its advantages and disadvantages, and it really depends on how you data is structured as to which approach you use.  You can also mix and match the different approaches as you see fit.



## Viewing an email



mail_view displays a preview of the email with the header information shown in the page header and the body in an iframe, as shown below.
![Mail Preview As HTML](https://s3.amazonaws.com/mail_preview_blog/MailPreviewAsHtml.png)


If you have provided a text and html template for the email, a drop-down is displayed in the page header to allow you to preview the different formats.  Here we are displaying the text version of the email
![Mail Preview As Text](https://s3.amazonaws.com/mail_preview_blog/MailPreviewAsText.png)


Since the body of the email is displayed in an [iframe](http://www.w3.org/wiki/HTML/Elements/iframe), clicking on a link in the email will open the link inside the iframe.
![Mail Preview Open Link](https://s3.amazonaws.com/mail_preview_blog/MailPreviewLinkInFrame.png)




## Summary



The [mail_view](https://github.com/basecamp/mail_view) gem is a great tool to allow you to visually inspect the emails sent by your Rails application.
