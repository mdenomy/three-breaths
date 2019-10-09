---
author: mdenomy
date: 2014-01-21 01:29:21+00:00
draft: false
title: Programmatically Clearing the Facebook Share Image Cache
type: post
url: /2014/01/20/programmatically-clearing-the-facebook-share-image-cache/
tags:
- Social Media
tags:
- Facebook
- OpenGraph
---

When you share a URL on Facebook, it scrapes the page for the URL for the [Open Graph data](https://developers.facebook.com/docs/web/tutorials/scrumptious/open-graph-object/) to determine what image/video to display.  Facebook caches the image for that URL, so if you change the image and then share the same URL at a later time, the old image will still get displayed, which is probably not what you want to do.

Facebook provides the [Open Graph Debug Tool](https://developers.facebook.com/tools/debug/) that can be used to manually clear the cached value for the URL, but that may not be a workable if your website allows images to be changed dynamically.  Ideally, you would want a way to programmatically clear the cache after the associated image is changed.

Fortunately, there is a way to clear the cache using the OpenGraph API by [forcing a scrape of the URL](https://developers.facebook.com/docs/opengraph/using-objects#selfhosted-update). The key is to set the **'scrape'** parameter to true in the API call. The following Ruby code assumes that the Facebook application id and secret are stored in environment variables.

**facebook_open_graph.rb**

    
    module FacebookOpenGraph
      def self.clear_cache(url)
        params = {
          :client_id => ENV['FACEBOOK_APP_ID'],
          :client_secret => ENV['FACEBOOK_SECRET'],
          :grant_type => "client_credentials"
        }
        uri = URI("https://graph.facebook.com/oauth/access_token?#{params.to_query}")
        response = Net::HTTP.get(uri)
        access_token = Rack::Utils.parse_nested_query(response)["access_token"]
        unless access_token.nil?
          uri = URI('https://graph.facebook.com')
          res = Net::HTTP.post_form(uri, 'id' => "#{url}", 'scrape' => 'true',
              'access_token' => "#{access_token}", 'max' => '500')
        end
      end
    end


Then to clear the cache you merely need to call the clear_cache method, passing in the URL being shared.

    
    FacebookOpenGraph.clear_cache("http://myurl.com/some_cool_page")
