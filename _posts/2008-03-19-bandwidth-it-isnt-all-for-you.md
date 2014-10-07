---
title: 'Bandwidth, it isn&#8217;t all for you.'
author: Ara Pehlivanian
layout: post
permalink: /bandwidth-it-isnt-all-for-you/
tags:
  - bandwidth
  - optimization
  - performance
  - speed
  - web development
  - yahoo exceptional performance
yourls_shorturl:
  - http://a12n.com/5f
categories:
  - General
---
I love web development best practices. I&#8217;m always looking for better, more efficient and more reliable ways of doing things. Gaining that knowledge isn&#8217;t enough though, I want to educate others about it. But I often find that it&#8217;s difficult to illustrate my point without concrete examples for why it&#8217;s better to do something one way instead of another. Well I found a half-decent real-life example today for why optimization is a good thing.

It happened when I was trying to visit a site and noticed a long delay in its loading time. Immediately I realized that iTunes was downloading 3 podcasts (since I have it set to auto update every hour) and in the process monopolizing my home DSL. That&#8217;s when it clicked, *your site is likely not the only thing coming down the pipe when it&#8217;s being loaded.* It&#8217;s probably coming through at the same time as streaming music, another site or two, and maybe even few file downloads. So really, at any given moment, you probably *are* coming through at 56k, if you&#8217;re lucky.

Something to consider the next time you&#8217;re tempted to balk at optimization.