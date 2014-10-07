---
title: 'The graceful degradation myth [UPDATE]'
author: Ara Pehlivanian
excerpt: Watch out for JavaScript and CSS interdependence, you just might be locking people out.
layout: post
permalink: /the-graceful-degradation-myth/
tags:
  - Accessibility
  - css
  - javascript
  - web development
yourls_shorturl:
  - http://a12n.com/21
categories:
  - General
---
<p style="padding: .5em; border: solid 1px #000; -moz-border-radius: .5em;">
  <strong style="color: #f00">Update:</strong> Read the latest developments on this subject here: &#8220;<a href="http://arapehlivanian.com/2007/02/14/understanding-and-solving-the-javascriptcss-entanglement-phenomenon/">Understanding and solving the JavaScript/CSS entanglement phenomenon</a>&#8220;
</p>

Building pages with HTML for structure, CSS for presentation and JavaScript for behaviour is the way to go. As far as I&#8217;m concerned it&#8217;s the *only* way to build web pages. But be warned, every layer brings with it an added level of complexity. Not only in what each technology can do, but in how they interact with each other. Case in point, you build a page with multiple states&#8212;say a tab driven box&#8212;and hide every one of them except the first via CSS. You then use DOM scripting (JavaScript) to show/hide the other states. So in other words, when one of the tabs are clicked, the corresponding content for that tab appears. Wonderful, but there&#8217;s a catch. We all know that &#8220;graceful degradation&#8221; means that you&#8217;ll be able to see all of those states if you don&#8217;t have CSS. But what if you don&#8217;t have JavaScript? By hiding the other states via a CSS instruction and then tying their appearance to a JavaScript function, you&#8217;ve essentially limited the graceful degradation of your page to only those who have JavaScript. Those without will never see the other states since they&#8217;re hidden by default.

The workaround of course is messy at best. You could either load a separate stylesheet with the rules for the hidden states via JavaScript or even assign the class names and/or style rules directly via the DOM but both of these methods require a) code and b) the use of the onload event. The problem with the onload event is that for pages with a lot of content, you&#8217;ll see a flicker. In other words, the content will load up and then all but the first state will be hidden right before the visitor&#8217;s eyes. Not the ideal situation. The alternative of course is to mess up your `<body>`with `<script>` tags which goes against the Web Standards ethos of separation of structure, presentation and behaviour.

So what are we left with? I call it a myth. Because though it may sound really nice to say that Web Standards allows for graceful degradation, the reality is that as soon as you get into anything more complex than a simple page, you&#8217;re liable to get into trouble.