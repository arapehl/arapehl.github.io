---
title: Automated JavaScript Vertical Flip Image Reflection
author: Ara Pehlivanian
excerpt: Web 2.0 will never be the same again
layout: post
permalink: /automated-vertical-flip-image-reflection/
tags:
  - canvas
  - javascript
  - web development
yourls_shorturl:
  - http://a12n.com/9
categories:
  - General
---
<p class="embellished0">
  <img src="http://arapehlivanian.com/wp-content/uploads/2007/02/me.jpg" alt="Me" />Do you see it? Look closely, now do you see it? Look <a href="http://arapehlivanian.com/2007/01/26/firebug-turns-1/">around</a> <a href="http://arapehlivanian.com/2007/01/19/some-of-the-best-advice-ive-received/">the site</a> <a href="http://arapehlivanian.com/2006/10/03/google-talk-voicemail/">a little</a>. If you&#8217;re using either Firefox 1.5+, Safari or Opera 9+ you should be seeing a reflection under the images in the post body&#8211;thanks to the Reflection script I just wrote. No Java applets, no Flash, just pure JavaScript. And it&#8217;s relatively light and fast too&#8211;each reflection consists of just one new DOM element. Here, check out this <a href="http://arapehlivanian.com/scripts/reflect/reflect.html">example page</a>.
</p>

The script allows you to modify opacity and depth and comes with three different ways of passing images to the reflection object (by ID, by class name or just a raw array you build yourself).

A basic implementation looks like this:

    <script type="text/javascript" src="reflect.js"></script>
    window.onload = function(){
    	var reflections = new ARA.effects.Reflection();
    		reflections.addImage("myImageID");
    		reflections.reflect();
    }

A more advanced implementation looks like this:

    <script type="text/javascript" src="reflect.js"></script>
    window.onload = function(){
    	var reflections = new ARA.effects.Reflection();
    		reflections.addImage("me");
    		var imgs = [];
    			imgs.push(document.getElementById("csarvenWLGreen"));
    			imgs.push(document.getElementById("microformats"));
    		reflections.addImagesRaw(imgs);
    		reflections.addImagesByClassName("reflect");
    		reflections.addImagesByClassName("reflect1", {startPoint:"group",alpha:.75,depth:10});
    		reflections.reflect();
    }

The JavaScript code is documented as well so you should be able to get a head start. I&#8217;ll write up more detailed docs if and when interest grows. If you&#8217;re interested in implementing it on your own site you can download the [reflect.js][1] file or the entire [zipped example][2]. Remember, the script only works on Firefox 1.5+, Opera 9+ and Safari (though I&#8217;ve only tested it on Firefox so let me know if it works on the others).

Enjoy! And as always, your feedback would be much appreciated.

<!-- wp_ad_camp_1 -->

**Update**: In a turn of dumb misfortune, I found out **after** releasing this, that someone had already coded an [extremely similar implementation][3] (with IE support) last year! Oh well, you do what you can I guess&#8230;

 [1]: http://arapehlivanian.com/scripts/reflect/reflect.js
 [2]: http://arapehlivanian.com/scripts/reflect.zip
 [3]: http://cow.neondragon.net/index.php/1343-Reflectionjs-16