---
title: Hacking the Technorati Badge part Deux
author: Ara Pehlivanian
layout: post
permalink: /hacking-the-technorati-badge-part-deux/
tags:
  - javascript
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/6i
categories:
  - General
---
<ins datetime="2006-05-12T05:35:02+00:00">The code below is out of date. For the latest version see <a href="http://arapehlivanian.com/2006/05/12/documentwrite-fix-for-real-xhtml/">document.write() fix for (real) XHTML</a></ins>  
In my previous post on [Hacking the Technorati Badge][1] I told the tale of how I managed to get it working with the application/xhtml+xml MIME type. Since then I tweaked the technique and managed to get rid of the extra `<script>` tag immediately preceding the XHTML element you want badge to appear in. I was able to do this by identifying the word &#8220;technorati&#8221; in the `src` attribute of the `<script>` tag and then inserting the contents of the badge immediately next to it.

Here&#8217;s the updated code:

    var Utils = {
    	DW : function(str){
    		var s = document.body.getElementsByTagName("script");
    		for(var i=0; i < s.length; i++){
    			if(s[i].getAttribute("src").toLowerCase().indexOf("technorati") != -1){
    				str = Utils.CleanTechnorati(str);
    				s[i].parentNode.innerHTML += str;
    			}
    		}
    	},
    	CleanTechnorati : function(str){
    		return str.substring(0, str.indexOf("&#187")+5) + ";" + str.substring(str.indexOf("&#187")+5, str.length);
    	}
    }
    document.write = Utils.DW;

The reason for this is because about a day after I implemented the fix I noticed [my Silktide score][2] go down by .6 points. When I looked into it I saw that it&#8217;s because according to the British Disability Discrimination Act you can&#8217;t have `<script>` tags directly in the page&#8217;s `<body>` (this makes no sense since the Technorati badge is inserted via a `<script>` tag). And since this code is found on all of my pages, it hit my score pretty hard. So out goes the extra `<script>` tag.

Now to see what I can do about badges with multiple `document.write()`s

 [1]: http://arapehlivanian.com/2006/04/26/hacking-the-technorati-badge/ "Hacking the Technorati Badge or: How I Hacked Document.Write() in Order to Make it Work With application/xhtml+xml"
 [2]: http://www.silktide.com/index.php?node=18444&#038;form2=1&#038;staticq=1&#038;f2_url=http%3A%2F%2Farapehlivanian.com