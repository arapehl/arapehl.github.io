---
title: Sidebar Semantic Shenanigans
author: Ara Pehlivanian
layout: post
permalink: /sidebar-semantic-shenanigans/
featurepic:
  - wp-content/plugins/the_feature/featurepics/._kiwi-beta.gif
featuretitle:
  - Sidebar Semantic Shenanigans
tags:
  - css
  - semantics
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/7m
categories:
  - General
---
The ever-present sidebar. It&#8217;s a staple of the &#8216;net. You see it everywhere. It&#8217;s an accepted design convention allowing visitors to quickly recognize it among millions of sites as a place to find all kinds of auxiliary information.

Now we&#8217;re all aware of the importance of [keeping our classes clean][1], meaning that they shouldn&#8217;t contain presentational information like &#8220;leftbox&#8221; or &#8220;greentext&#8221;, but what about something a little less obvious like &#8220;sidebar?&#8221; I&#8217;ve&#8212;slowly&#8212;come to realize that the ubiquitous sidebar&#8217;s name is presentational. I mean the word &#8220;side&#8221; can mean only one of two things: left, or right. Just because it doesn&#8217;t say &#8220;left&#8221; or &#8220;right&#8221; doesn&#8217;t mean the word &#8220;side&#8221; isn&#8217;t implying one of them.

Semantically speaking however, what&#8217;s being presented in the &#8220;sidebar&#8221; has nothing to do with the word &#8220;side&#8221;, but is most often auxiliary information that is usually&#8212;but not always&#8212;related to the main content block. Hence my decision to name the sidebar on my site &#8220;aux-content.&#8221; This way, it&#8217;s fully autonomous in terms of its ID (I don&#8217;t believe in using class names for unique items in a page) and isn&#8217;t bound to be a *side*bar for the rest of its life.

Now if your sidebar only contained the most recent posts for example, or your blogroll and nothing else, then you could easily name its ID &#8220;recent-posts&#8221; or &#8220;blogroll.&#8221; But it should never be named &#8220;sidebar.&#8221; I mean, what if you wanted to turn it into a footer one day, or a part of the header, or something else? 

Go semantic, it&#8217;s your safest bet.

 [1]: http://meyerweb.com/eric/thoughts/2005/02/23/keep-your-classes-clean/