---
title: Introducing 140 char (or less) JavaScript programs
author: Ara Pehlivanian
layout: post
permalink: /introducing-140-char-or-less-javascript-programs/
yourls_shorturl:
  - http://a12n.com/3u
categories:
  - General
tags:
  - challenge
  - javascript
  - protest
  - twitter
---
Today I got tired of seeing yet another `onclick="obtrusivejavascript()"` in HTML so I [wrote a little program in protest][1]. What I wanted to do though was to post the program to Twitter which has a 140 character limit so it was mildly challenging. Here it is:

Fully expanded:

    var elems = document.getElementsByTagName("*");
    for (var i = 0; elems[i]; i += 1) {
        if (elems[i].getAttribute("onclick")) {
            elems[i].onclick = function () {
                alert("FAIL!");
            }
        }
    }

Compressed for Twitter:

    var x=document.getElementsByTagName("*");for (var i=0;x[i];i++){if (x[i].getAttribute("onclick")){x[i].onclick=function(){alert("FAIL!");}}}

I invite you to continue the trend. Write 140 character (or less) JavaScript programs and post them to Twitter then post a link here in the comments. If the trend grows, I&#8217;ll build a small site to host the activity.

I&#8217;ll go first!

 [1]: http://twitter.com/ara_p/statuses/861969980