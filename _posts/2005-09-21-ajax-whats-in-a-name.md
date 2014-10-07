---
title: 'AJAX: What&#8217;s in a name?'
author: Ara Pehlivanian
layout: post
permalink: /ajax-whats-in-a-name/
tags:
  - ajax
  - dom
  - javascript
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/39
categories:
  - General
---
What do a [Greek hero][1], a [town in Ontario][2], a [household cleaner][3], a [play by Sophocles][4], and the revival of JavaScript have in common? They all bear the name [AJAX][5].

I don&#8217;t know about you, but as much as I&#8217;m a sucker for buzzwords, I just can&#8217;t bring myself to use the acronym AJAX in a conversation without feeling like a sellout. Maybe it&#8217;s because the closer I look at AJAX, the less the acronym seems to apply.

Take the &#8220;X&#8221; in AJAX. It stands for XML, but a lot of &#8220;AJAX&#8221; apps being built aren&#8217;t transferring XML via the famed [XMLHTTP][6]. Rather, they use an IFrame to make the connection and the data is in the form of [JSON][7], HTML or even just plain old text. In whose case the acronym should change to AJAJ, AJAH and AJAT respectively. But it doesn&#8217;t, and so I&#8217;m stuck saying &#8220;AJAX&#8221; when I really mean &#8220;AJAJ.&#8221;

Likewise, the asynchrony of some AJAX apps is also iffy at best. Though they fetch data after the page has loaded, they still rely on the user&#8217;s input and the fetch tends to be pretty synchronous. [Amazon&#8217;s diamond search][8] is an example of the JS code fetching data only when the client modifies the search filters. While [Google Maps][9] only loads data when you move the map. To the best of my understanding of the word asynchronous, these apps seem pretty synchronous to me.

<ins datetime="2005-10-10T22:22:00-05:00">After writing this article I realized that the XMLHTTP protocol actually makes async calls. So again, it&#8217;s only AJAX if you use XMLHTTP.</ins>

I can&#8217;t harp on Google though. They never claimed to be doing any AJAX. Their engineers just [call what they&#8217;re doing][10] JavaScript. Which in effect, is all it really is. Which is why I personally refer to the AJAX phenomenon quite simply as the revival of JavaScript.

Ultimately, once you come up with an acronym, you set boundaries (however ethereal) on something that&#8217;s capable of doing so much more.

 [1]: http://www.answers.com/topic/ajax-4
 [2]: http://www.answers.com/topic/ajax-ontario?hl=ajax
 [3]: http://www.colgate.com/app/Colgate/US/HC/Products/HouseholdCleaners/Ajax.cvsp
 [4]: http://www.answers.com/topic/ajax-sophocles?method=6
 [5]: http://www.answers.com/topic/ajax-3?method=6
 [6]: http://www.answers.com/XMLHTTP
 [7]: http://www.answers.com/JSON
 [8]: http://www.amazon.com/gp/gsl/search/finder/002-6525933-5713644?productGroupID=loose%5fdiamonds
 [9]: http://maps.google.com/
 [10]: http://news.com.com/Will+AJAX+help+Google+clean+up/2100-1032_3-5621010.html