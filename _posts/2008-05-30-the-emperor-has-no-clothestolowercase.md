---
title: '&#8220;THE EMPEROR HAS NO CLOTHES&#8221;.toLowerCase()'
author: Ara Pehlivanian
layout: post
permalink: /the-emperor-has-no-clothestolowercase/
yourls_shorturl:
  - http://a12n.com/5p
categories:
  - General
tags:
  - General
---
In JavaScript, when you want to know what a given element&#8217;s node name is, you use its `nodeName` property. Now as far as I can tell, it always returns the node&#8217;s name in uppercase, so an anchor&#8217;s node name returns as `A` and a table&#8217;s `TABLE`. I have yet to see a browser return a node name in lower case or mixed case. So here&#8217;s my question, why is it that I keep seeing the following code all over the internet?

    if (el.nodeName.toLowerCase() === "table") {

Is it because there actually *are* edge cases where browsers return node names in something other than uppercase? Or is it because we just want to be sure, and in our paranoia we normalize the returned value just in case? I want to know because though it may only cost milliseconds at best, `toLowerCase` is still an extra method that needs to be executed whenever a node name is checked, and it could get heavy inside large loops (now *I&#8217;m* being paranoid). It&#8217;s also cumbersome and annoying to have to write, especially if it isn&#8217;t needed. I&#8217;d much rather leave it at:

    if (el.nodeName === "TABLE") {

So *is* there a reason, or are we all just to scared to say &#8220;the Emperor has no clothes?&#8221;