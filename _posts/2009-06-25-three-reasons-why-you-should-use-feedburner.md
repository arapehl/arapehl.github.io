---
title: Three Reasons Why You Should Use FeedBurner
author: Ara Pehlivanian
layout: post
permalink: /three-reasons-why-you-should-use-feedburner/
subhead:
  - Here are three advantages to using a service such as FeedBurner.
yourls_shorturl:
  - http://a12n.com/1u
categories:
  - Technology
tags:
  - atom
  - explanations
  - feedburner
  - feeds
  - rss
---
I just wrote a post on [creating a feed using YQL and Pipes][1]. Now that you&#8217;ve got a shiny new feed, what to do with it? Well, my suggestion is to run it through a service like [FeedBurner][2], here are three reasons why:

## Cleaner URL

What you may have noticed if you read that post is the not-so-pretty URL that Pipes generates. I mean don&#8217;t get me wrong, Pipes is great but wouldn&#8217;t it be great to have a URL that looked like this,

`http://pipes.yahoo.com/feeds/myImaginaryFeed`

instead of this?

`http://pipes.yahoo.com/pipes/pipe.run?_id=05ed54b00bf80cc43160ee19d6b18e02&_render=rss`

Well, you&#8217;re in luck because running a feed through FeedBurner will give you a nice URL like this,

`http://feeds.feedburner.com/myImaginaryFeed`

## Usage Stats

But wait, there&#8217;s more!  (Sorry, I couldn&#8217;t help it.) FeedBurner&#8217;s main purpose as a service isn&#8217;t really to give you cleaner URLs, it&#8217;s to &#8220;analyze, optimize, publicize,&#8221; and &#8220;monetize&#8221; your feed. One of the great things about using FeedBurner is that any usage of a feed gets logged giving you usage stats, something darn near impossible otherwise. (Unless of course you&#8217;re a server-side code ninja and love writing code for this sort of thing, but then you&#8217;re not the target audience for this post anyway so go code something already will ya?)

[<img class="alignnone size-medium wp-image-807" title="feedburner" src="http://arapehlivanian.com/wp-content/uploads/2009/06/feedburner-259x300.png" alt="feedburner" width="259" height="300" />][3]

## Abstraction

Finally, using FeedBurner gives you the added advantage of being able to provide a URL for your feed that never changes. Since your actual feed is plugged into FeedBurner and you&#8217;re providing your readers with the URL created by the service rather than your own, you can easily change your source feed URL without losing any readers. They&#8217;ll always be plugged into your FeedBurner feed no matter what the source is. Instant feed URL abstraction!

 [1]: http://arapehlivanian.com/2009/06/25/screen-scraping-and-creating-a-feed-with-yql-and-yahoo-pipes/
 [2]: http://www.feedburner.com/
 [3]: http://arapehlivanian.com/wp-content/uploads/2009/06/feedburner.png