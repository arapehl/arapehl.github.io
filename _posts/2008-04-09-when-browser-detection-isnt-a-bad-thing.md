---
title: 'When Browser Detection Isn&#8217;t a Bad Thing'
author: Ara Pehlivanian
layout: post
permalink: /when-browser-detection-isnt-a-bad-thing/
tags:
  - best practices
  - browser detection
  - code fork
  - cross-browser
  - css
  - feature detection
  - javascript
  - sniffing
  - web development
yourls_shorturl:
  - http://a12n.com/3n
categories:
  - General
---
One of the pillars of the Web Standards movement&#8211;reinforced in [Zeldman][1]&#8216;s seminal [Designing With Web Standards][2]<img src="http://www.assoc-amazon.ca/e/ir?t=arapehli-20&l=ur2&o=15" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />&#8211;is the idea that browser detection is a bad thing and should be avoided. As with another idea spawned at around the same time, that &#8220;tables are bad&#8221;, it isn&#8217;t wholely true. There are situations where tables are good and even appropriate, likewise there are situations where browser detection is appropriate.

### Old School: Browser Detection

Traditionally, browser detection was used for code forking in order to support two or more highly incompatible browsers. So if Netscape 3 was detected, one block of JavaScript was executed, and if Internet Explorer 3 was detected then an entirely different block of JavaScript was executed. The trouble with this model was, and still is, that it&#8217;s expensive to maintain. To say nothing of it being error prone. It also doesn&#8217;t do a great job of anticipating future versions of browsers.

An example of this was on the [Microsoft Games][3] site. Visiting it with the new beta of Internet Explorer 7 would cause the site to hide its content and display a message asking that the visitor please *upgrade* to Internet Explorer 6 or newer.

### New School: Feature Detection

The alternative to browser detection is feature detection. Feature detection means checking to see if a feature exists prior to implementing it. So for example, if a developer wanted to use `getElementById`, he&#8217;d first check for it like so:

    if (document.getElementById) {
        var foo = document.getElementById("foo");
    }

### The *New* Browser Detection

This works great, unless a browser says it *can* do something and actually *can&#8217;t*. In other words, if browser X implemented `getElementById` but it was buggy, it would still pass the test but fail in the code. This is where browser detection comes back into play, but not like in the bad old days. No, this time around browser detection would be used to target and fix&#8211;or deny&#8211;a feature in a browser known to have issues with it.

An example of this sort of thing would be Safari 2.x&#8217;s trouble with `cellIndex`. Normally, checking a table cell&#8217;s `cellIndex` property would return a number representing its position within a row. Not so with Safari 2.x, in its case `cellIndex` always returns 0. So testing for `cellIndex` doesn&#8217;t help since it *is* there, it just doesn&#8217;t work.

There are also edge cases that simply *can&#8217;t* be tested for. For example, background images inside an animated `iframe` in Internet Explorer 6 will flicker throughout the animation sequence. There is no way to do feature detection in this case, however the issue is known. So, the solution may well be to simply test for the browser and if Internet Explorer 6 is detected, to simply deny it the animation and just snap to the last frame.

### Summary

So, the *new* browser detection if you will, is all about **damage control** in cases where features can&#8217;t be detected yet problems are known to exist. I those cases, specific versions of specific browsers are targeted and dealt with appropriately. The mechanism for this may be in the form of [conditional comments][4] or JavaScript code written for the purpose.

 [1]: http://zeldman.com/
 [2]: http://www.amazon.ca/gp/redirect.html?ie=UTF8&#038;location=http%3A%2F%2Fwww.amazon.ca%2FDesigning-Web-Standards-Jeffrey-Zeldman%2Fdp%2F0321385551%3Fie%3DUTF8%26s%3Dbooks%26qid%3D1207708730%26sr%3D8-1&#038;tag=arapehli-20&#038;linkCode=ur2&#038;camp=15121&#038;creative=330641
 [3]: http://www.microsoft.com/games/
 [4]: http://blogs.msdn.com/ie/archive/2005/10/12/480242.aspx