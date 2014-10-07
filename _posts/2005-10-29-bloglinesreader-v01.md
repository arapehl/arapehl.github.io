---
title: BloglinesReader v0.1
author: Ara Pehlivanian
layout: post
permalink: /bloglinesreader-v01/
tags:
  - plugins
  - reviews
  - syndication
yourls_shorturl:
  - http://a12n.com/72
---
Ever search the web for a tool that performs a specific function only to find all manner of things that just fall short? As you&#8217;re most likely aware I&#8217;m in the middle of &#8220;[moving in][1]&#8221; and am customizing [WordPress][2] as a result. Like anyone else, I wanted to put up a blogroll but found that WordPress didn&#8217;t do quite what I needed it to. Sure, it allowed me to import an OPML file with my feeds, but that meant that if I updated my aggregator ([Bloglines][3]) with a new feed I&#8217;d need to manually add its link to my WP link list as well. Not fun and definitely not efficient. I just wanted my WP blogroll to reflect what was in my aggregator. The other problem was that WP didn&#8217;t allow me to delete more than one link at a time. I found this out a couple of days into playing with WP and **after** I imported my OPML. I wasn&#8217;t pleased with the import and had to manually delete upwards of 100 links. Not fun.

Bloglines has a &#8220;share&#8221; feature whereby it shares your feed list&#8212;or a part of it&#8212;via a bit of JavaScript. But I wanted my links to be part of my markup and semantically correct&#8212;unfortunately the list that the Bloglines&#8217; JS spits out is a series of divs.

So I searched the web for a plugin that would allow me to sync my aggregator&#8217;s feeds with WP. I found all kinds of gadgets that would randomly display a few links, or require you to keep a copy of your OPML locally until I came across [BloglinesReader v0.1][4] by [Coda Hale][5]. This little gem does exactly what I need it to. It just goes and grabs my feed list and incorporates it wherever I want&#8212;in this case my [links][6] page. It even caches the list locally so I don&#8217;t kill my bandwidth quota or hit Bloglines every time someone hits my links page.

If you&#8217;ve got WordPress and use Bloglines for your feed reading, I strongly recommend [BloglinesReader][4] for your blogroll.

 [1]: /categories/moving-in
 [2]: http://wordpress.org
 [3]: http://bloglines.com
 [4]: http://blog.codahale.com/2005/09/25/bloglinesreader-v01/
 [5]: http://blog.codahale.com/
 [6]: /links/