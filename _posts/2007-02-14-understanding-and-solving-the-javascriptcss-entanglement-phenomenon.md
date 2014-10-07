---
title: Understanding and solving the JavaScript/CSS entanglement phenomenon
author: Ara Pehlivanian
excerpt: Keeping the three layers of separation truly separate.
layout: post
permalink: /understanding-and-solving-the-javascriptcss-entanglement-phenomenon/
tags:
  - Accessibility
  - css
  - javascript
  - web development
yourls_shorturl:
  - http://a12n.com/m
categories:
  - General
---
About a year ago I wrote &#8220;[The graceful degradation myth][1]&#8221; in which I talked about the entanglement phenomenon that occurs when you mix JavaScript functionality with CSS &#8220;initial states&#8221;. By that I mean, if you&#8217;ve got a block of content that is initially hidden via CSS (i.e. `display: none;`) and is only made visible through JavaScript functionality (like an `onclick` event), you run the risk of barring access to that hidden content to visitors who don&#8217;t have JavaScript running on their browser&#8211;if you don&#8217;t do it right that is.

Since I wrote that post I came up with a technique that solved the problem (as well as the [&#8220;flicker&#8221; problem][2] that occurs with some fixes). This past week I came up with what I believe is an even better solution which I plan on using in upcoming projects. I&#8217;ll share both with you here in this post.

### How to layer

Before I get to the solutions, I&#8217;d like to touch briefly on the subject of the three layers of separation. Those being of course content (HTML), presentation (CSS), and behaviour (JavaScript). Most people in the web standards community know of these, but what I seldom hear is the idea that one layer should never break the other. See, you start with HTML on top of which you place CSS and then comes JavaScript (if you&#8217;re using all three that is, though the sequence of the last two is debatable). When you go from CSS to JavaScript you should never do something in the CSS that relies on the JavaScript. In other words, dependency should be unidirectional&#8211;downward. A layer should only be dependent on one that it&#8217;s applied to, not the other way around. Therefore, when implementing a show/hide mechanism in the behavioural layer, you should do so in a way that still allows the first two layers to be accessible should the third not be available.

The reason I just covered the three layers of separation is because a lot of JavaScript implementations break the rule of non obstruction. A lot of implementations will hide content in CSS and only make it available through JavaScript, thus tangling the two layers together and breaking the separation model. The following solutions avoid this phenomenon.

### The first solution

Create a CSS file that will contain all of the &#8220;initial state&#8221; rules for your behavioural layer. So for example in the case of a flyout menu system, if all sub-menus with the class name &#8220;flyout&#8221; are to be initially hidden when the page loads your CSS file would contain the following rule:

    .flyout{display: none;}

Then, link the CSS file to your page using JavaScript. That way, if JavaScript isn&#8217;t available the CSS file never gets loaded and the rule never gets applied. Thus the content remains visible and accessible. The way I used to do this was with the following line of JavaScript code in the <head> of the page:

    document.write("<link rel='stylesheet' href='initial_states.css' type='text/css' \/>");

The problem with this technique is that I&#8217;m using `document.write()` which is bad. It&#8217;s bad because it ties the instruction to a specific place in the document, it&#8217;s archaic and isn&#8217;t supported in pure XHTML implementations (such as this site that&#8217;s delivered with the `application/xhtml+xml` MIME type).

### The better solution

The better solution builds on the basic concept of the original but does it without `document.write()`. This time your initial state CSS rules will look like this:

    body.hasJS .flyout{display: none;}

And you can go ahead and load the CSS file in the traditional way without using JavaScript. The key rather is to assign the &#8220;`hasJS`&#8221; class to the body element through JavaScript. If JavaScript doesn&#8217;t exist, it doesn&#8217;t get set and the rule doesn&#8217;t get applied. You can still keep the initial states in a separate file if you&#8217;d like but it isn&#8217;t necessary. So long as the rule exists somewhere. The simplest implementation of this technique is to have the following line of JavaScript code on the first line inside the body element:

    document.body.className += "hasJS";

The reason for this is because doing it in an `onload` event will cause a flicker where the page will load, then the content will be hidden. This way, the class is applied before any content is parsed. There are of course better ways of applying the class name (such as an `addClassName()` function that only adds the class name if it doesn&#8217;t already exist).

I haven&#8217;t fully tested the better technique on a wide variety of platforms as I have with the standard one, so if you have any success with it, please let me know.

I&#8217;ve mocked up a quick [example page][3] so you can see it in action.

 [1]: http://arapehlivanian.com/2006/02/09/the-graceful-degradation-myth/
 [2]: http://www.barelyfitz.com/blog/archives/2006/03/09/232/
 [3]: http://arapehlivanian.com/wp-content/uploads/2007/02/nojscss.html "Example page"