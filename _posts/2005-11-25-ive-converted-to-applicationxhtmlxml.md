---
title: 'I&#8217;ve converted to application/xhtml+xml'
author: Ara Pehlivanian
excerpt: "I've taken the leap. The site is now offered in the application/xhtml+xml MIME type to all compliant browsers."
layout: post
permalink: /ive-converted-to-applicationxhtmlxml/
tags:
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/20
categories:
  - General
---
So I&#8217;ve gone ahead and decided what to do about my [dilemma][1]. I&#8217;m now serving my pages using the `application/xhtml+xml` MIME type to compliant browsers and the `text/html` MIME type to everything else. In order to be able to do this, I installed a wonderful little plugin called [WP Content Negotiator][2] written by Admiral Justin. It feels like I just got my first tattoo. It&#8217;s a combination of feeling like &#8220;wow, I did it!&#8221; and &#8220;oh boy, I hope I don&#8217;t regret this.&#8221;

I have to say though that I really learned the meaning of the expression &#8220;be careful what you wish for.&#8221; A while ago in my post [Invalid markup: does it matter?][3] I was complaining about how we should have <q cite="http://arapehlivanian.com/2005/09/27/invalid-markup-does-it-matter/">zero tolerance for invalid markup</q>, and that browsers were too lax with tag soup. Well, let me tell you, installing this plugin was a slap in the face for yours truly. If ever there was a surefire way to break my site right quick, this was it. Colour me shamed. I also learned another valuable lesson: &#8220;never install plugins directly on the production version of your site, you&#8217;ll most likely break it.&#8221; 

So there I was, with this giant error message staring me down because the XML parser I had just invoked in Firefox didn&#8217;t like my markup. Horror of horrors, I just realized that I couldn&#8217;t get by with even one error in my markup. So a little nail-biting, and some quick fixes later, the site is fully XHTML 1.1 Strict served with the `application/xhtml+xml` MIME type. Not without some consequences however. For example, I can no longer run AdSense or Technorati JavaScripts because of the way they try to write to the DOM. It just doesn&#8217;t work the same way with the XML DOM and I have yet to figure out what to do about it. Unfortunately, according to Alex Stevenson&#8217;s experience, it seems that [Google isn&#8217;t about to fix the AdSense XHTML compatibility problem][4].

It&#8217;s a very awkward feeling though, to know that at any given moment, a lapse in my markup will cause a page to stop working. Of course, you might be asking yourself: &#8220;why do something like that?&#8221; Well, like I told a friend earlier today, &#8220;my site is my indulgence, and it&#8217;s where I can exercise my purist tendencies.&#8221; Sure it&#8217;s fanatical to a fault, but hey, where else am I going to have the fun of experimenting with the new and chic? Besides, I can always go back to boring old `text/html` whenever I want. But where&#8217;s the challenge in that?

 [1]: http://arapehlivanian.com/2005/11/22/html-or-xhtml-a-purists-dilemma/
 [2]: http://www.admiraljustin.net/con-neg/
 [3]: http://arapehlivanian.com/2005/09/27/invalid-markup-does-it-matter/
 [4]: http://www.fusionsite.co.uk/design/adsense_xhtml_strict.php