---
title: 'Hacking the Technorati Badge or: How I Hacked Document.Write() in Order to Make it Work With application/xhtml+xml'
author: Ara Pehlivanian
excerpt: "Technorati, like Google's AdSense uses JavaScript to insert content into your site via the document.write() method. Unfortunately document.write() isn't supported in the XML DOM (which is what this site uses when viewed in Firefox when served with the application/xhtml+xml MIME Type). Well, I hacked the document.write() method to circumvent the problem."
layout: post
permalink: /hacking-the-technorati-badge/
autometa:
  - javascript, document-write, technorati, technorati-badge, hack, hacks
tags:
  - javascript
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/1g
categories:
  - General
---
<ins datetime="2006-05-02T16:37:31+00:00">I&#8217;ve reworked this code to make it unobtrusive and consequently lighter. See &#8220;<a href="http://arapehlivanian.com/2006/05/02/hacking-the-technorati-badge-part-deux/">Hacking the Technorati Badge part Deux</a>&#8221; to read about it.</ins>  
The first thing I noticed when I [switched to application/xhtml+xml][1] was how unforgiving the XML parser is with badly formed markup. It stops parsing and displays a big fat red error message where your page is supposed to be. The second thing I noticed was how my nifty little third party JavaScript includes all stopped working. I&#8217;m talking of course about my AdSense ads and my Technorati Badge (which is now back in my footer thank-you-very-much).

Looking into the mystery disappearance I found that I was getting a bunch of JavaScript errors like this:

<code style="color: #ff0000">uncaught exception: [Exception... "Object cannot be created in this context" code: "9" nsresult: "0x80530009 (NS_ERROR_DOM_NOT_SUPPORTED_ERR)" location:...</code>

Putting two and two together I realized that &#8220;Object cannot be created in this context&#8221; and &#8220;ERROR\_DOM\_NOT_SUPPORTED&#8221; meant that JavaScript&#8217;s `document.write()` method wasn&#8217;t supported in the XML DOM.

Well, after a few frustrating evenings of trying to write a string-to-html-DOM-nodes parser in JavaScript (yes, I can be that dumb sometimes) and a few philosophical discussions with [Mathieu][2], I finally gave up. That is until he gave me the key to fixing this problem. You see, I got pretty far in my string-to-html-DOM-nodes parser work. The problem wasn&#8217;t that. The problem I was having&#8211;and what Mathieu so deftly solved&#8211;was in identifying where the `document.write()` was occuring. Maybe it would help at this point if I told you that my solution to getting `document.write()` working in `application/xhtml+xml` was to override the `document.write()` method and redirect it through a function of my own. That way I could manage what it did and essentially force it to play nice instead of crapping out. Every time I referred to `this` in my override code I just got the document object returned to me, rather than the DOM node that the script was being run in. (You know what I mean, when Technorati or AdSense tells you to just plop their ready-to-go, cut-and-paste <script> tag into your page.) So what, you may ask was Mathieu&#8217;s solution? A global variable set to the current script tag&#8217;s parent node&#8217;s ID. That way, the `document.write()` override could just grab that node and do its work inside it.

Then of course I also realized that I could replace my tedious, potentially error prone, and ultimately overkill code with a simple `.innerHTML` instead. That&#8217;s right, the non-standard workhorse `.innerHTML` which is [no worse than using the W3C&#8217;s DOM methods][3] (thanks PPK). So even though the purist in me was screaming for me to use my recursive beast of a node creator, the minimalist in me said &#8220;what are you crazy? Just use `.innerHTML`&#8220;.

Long story short (too late for that huh?) here&#8217;s the code. Oh and there&#8217;s an added function in there to clean up Technorati&#8217;s **broken** markup. Yes, you heard me, it&#8217;s broken.

### The JavaScript:

<pre>var Utils = {
	DWID : "",
	DW : function(str){
		var el = document.getElementById(Utils.DWID);
		str = Utils.CleanTechnorati(str);
		el.innerHTML = str;
	},
	CleanTechnorati : function(str){
		return str.substring(0, str.indexOf("&#187")+5) + ";" + str.substring(str.indexOf("&#187")+5, str.length);
	}
}
document.write = Utils.DW;</pre>

### The XHTML:

<pre>&lt;script type="text/javascript"&gt;Utils.DWID = "technorati_include";&lt;/script&gt;<br />
&lt;li id="technorati_include"&gt;&lt;script type="text/javascript" /&gt;&lt;/li&gt;</pre>

So basically, every time you&#8217;ve got a script you want to include, you just change the value of the global variable just before and assign it the script&#8217;s parent element&#8217;s ID and you&#8217;re all set! Enjoy!

 [1]: http://arapehlivanian.com/2005/11/25/ive-converted-to-applicationxhtmlxml/ "A previous blog post entitled: I’ve converted to application/xhtml+xml"
 [2]: http://www.zebrocratie.org/ "Mathieu Gagnon's Website"
 [3]: http://www.quirksmode.org/dom/innerhtml.html