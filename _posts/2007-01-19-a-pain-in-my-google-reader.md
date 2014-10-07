---
title: A Pain in my Google Reader
author: Ara Pehlivanian
excerpt: '"You should do your own tech support" -- Matt Mullenweg, The Future of Web Apps 2006'
layout: post
permalink: /a-pain-in-my-google-reader/
tags:
  - General
yourls_shorturl:
  - http://a12n.com/1t
categories:
  - General
---
<p class="embellished0">
  <img id="image268" src="http://arapehlivanian.com/wp-content/uploads/2007/01/googlereaderlogo.gif" alt="Google Reader Logo" />Recently I started pruning my RSS feeds. I was getting really discouraged by the deluge of stuff that I&#8217;d told myself I <em>should</em> be reading. Then I realized of course that I couldn&#8217;t possibly keep up with it all. So I chose the ones I read regularly, the ones that kept me the most informed and started cutting the rest. Or at least I tried to. Google Reader was throwing an error in Firefox that kept me from deleting feeds. It worked fine in IE though, so I went there and did some of the pruning. I also tried sending Google a report on the error so that they could fix it. Never heard back from them. So in the hopes that maybe someone from Google is <a href="http://googlereader.blogspot.com/2007/01/some-of-our-engineers-dont-work-at.html">scanning the blogosphere for articles on Google Reader</a>, here&#8217;s an exact copy of my report:
</p>

> Hi,
> 
> I&#8217;d like to report a bug in the Subscription Management page. I get the following JavaScript error when clicking the trash can next to a feed:
> 
>     e has no properties
>     Zc(["feed/http://xml.newsisfree.com//feeds/43/243.xml" ], Object)889806413-lens.js (line 180)
>     Xg( mouseup clientX=25, clientY=324)                             889806413-lens.js (line 172)
>     d--}}};w[_P].Zc=function(a,b){var c=Vc(a,"subs-label");for(var d=0,e;e=c[d];d++)...
> 
> I realize that the code&#8217;s obfuscated so the stack trace probably doesn&#8217;t tell you much, but I&#8217;m sure it&#8217;ll give you an idea as to the source of the problem. Here&#8217;s some browser/OS info on which I found the bug:
> 
> Browser: Firefox 1.5.0.9  
> OS: Microsoft Windows XP Professional (2002) SP2  
> JavaScript Console: Firebug Firefox Extension
> 
> Checking a box next to a feed and then clicking the &#8220;Unsubscribe&#8221; form button at the top of the page yields the exact same error (minus the stack trace).
> 
> I&#8217;ve also tried the same functionality with IE6 and it works fine. I hope you can find a solution (or tell me if I&#8217;m doing something wrong) so that I can resume using your service as soon as possible!
> 
> Thanks again for a great product!
> 
> Ara

Has anyone else had this problem?