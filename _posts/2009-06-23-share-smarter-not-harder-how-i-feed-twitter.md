---
title: 'Share Smarter, Not Harder: How I Feed Twitter'
author: Ara Pehlivanian
layout: post
permalink: /share-smarter-not-harder-how-i-feed-twitter/
subhead:
  - "I'm an automation nut, so it's no surprise that I've managed to automate sharing links on Twitter."
yourls_shorturl:
  - http://a12n.com/4t
categories:
  - Technology
tags:
  - automated
  - automation
  - feed
  - pipes
  - rss
  - twitter
  - yahoo pipes
  - yql
---
I was just a kid watching [DuckTales][1] when I heard [Scrooge McDuck say][2] &#8220;work smarter, not harder&#8221; and that philosophy stuck. Maybe it&#8217;s because I&#8217;m predisposed to avoid manual labour, who knows. All I know is I&#8217;m always on the lookout to simplify process. So when it came to sharing items of interest with friends, I grew tired of manually sending links one at a time over IM. Broadcasting over [Twitter][3] was slightly better but I ran the risk of [flooding][4] people with tweets. After all, we don&#8217;t consume media one bite-sized chunk at a time in neatly spaced intervals. We get random links from friends, watch video clips two or three at a time, browse [online stores full of really cool things][5] that we want, and so on.

What to do? The solution came to me in the form of a service called [Twitterfeed][6]. Twitterfeed lets you plug a feed into your Twitter account so that any time there&#8217;s a new item in the feed, it gets Tweeted to your account. Great, but there were still some issues to overcome, such as drawing all of my points of interest into one feed and then not flooding my Twitter account with a gzillion tweets.

## Step 1: The Funnel

Using a combination of [YQL][7] and [Yahoo! Pipes][8], I pulled in my Amazon [Wish List][9], Google Reader [shared items][10], [YouTube favourites][11], blog posts on [my site][12], and [Flickr favourites][13] into one giant feed.

[<img class="alignnone size-medium wp-image-786" title="twitter-funnel" src="http://arapehlivanian.com/wp-content/uploads/2009/06/twitter-funnel-300x166.png" alt="twitter-funnel" width="300" height="166" />][14]

## Step 2: Timed Release

Once Pipes gave me a consolidated feed, I was able to plug it into Twitterfeed. But I still had to make sure that Twitterfeed didn&#8217;t dump a bunch of tweets into Twitter at the same time. Luckily, Twitterfeed is customizable and I was able to tell it to release only one tweet every two hours. This way, whenever I marked several items in Google Reader as &#8220;shared&#8221; they got banked up and sent out one at a time over the course of the day.

[<img class="alignnone size-medium wp-image-787" title="twitterfeed" src="http://arapehlivanian.com/wp-content/uploads/2009/06/twitterfeed-300x187.png" alt="twitterfeed" width="300" height="187" />][15]

## Step 3: Letting People Know it&#8217;s Automated

I came across a bit of an odd phenomenon with this technique however. People thought I never slept because I was posting tweets like clockwork at all hours. It might be fun if people think you aren&#8217;t sleeping, but it isn&#8217;t as fun when they think you aren&#8217;t working. So I added &#8220;[AutoTweet]&#8221; to the end of the tweets that Twitterfeed posted (the service allows you to prefix and suffix tweets with text). That way, people could tell right away that I didn&#8217;t manually send out the tweet.

[<img class="alignnone size-medium wp-image-788" title="autotweet" src="http://arapehlivanian.com/wp-content/uploads/2009/06/autotweet-300x271.png" alt="autotweet" width="300" height="271" />][16]

That&#8217;s it! I didn&#8217;t get into too much technical detail here, but if you&#8217;re interested let me know and I&#8217;ll post a much more detailed writeup.

 [1]: http://en.wikipedia.org/wiki/DuckTales
 [2]: http://en.wikipedia.org/wiki/Scrooge_McDuck#Morality_and_beliefs
 [3]: http://twitter.com/
 [4]: http://en.wikipedia.org/wiki/Internet_Relay_Chat_flood
 [5]: http://www.thinkgeek.com/
 [6]: http://twitterfeed.com/
 [7]: http://developer.yahoo.com/yql/
 [8]: http://pipes.yahoo.com/pipes/
 [9]: http://www.amazon.com/wishlist/3LKFGZ8T05PWL
 [10]: http://www.google.com/reader/shared/01133275494082571067
 [11]: http://www.youtube.com/profile?user=arapehl&view=favorites
 [12]: http://arapehlivanian.com/
 [13]: http://www.flickr.com/photos/arapehl/favorites/
 [14]: http://arapehlivanian.com/wp-content/uploads/2009/06/twitter-funnel.png
 [15]: http://arapehlivanian.com/wp-content/uploads/2009/06/twitterfeed.png
 [16]: http://arapehlivanian.com/wp-content/uploads/2009/06/autotweet.png