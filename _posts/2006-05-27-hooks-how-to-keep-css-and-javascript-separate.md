---
title: 'Hooks: How to Keep CSS and JavaScript Separate'
author: Ara Pehlivanian
excerpt: Reinforcing the three layers of separation through the use of hooks.
layout: post
permalink: /hooks-how-to-keep-css-and-javascript-separate/
tags:
  - css
  - dom
  - javascript
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/3
categories:
  - General
---
<p class="embellished0">
  <img id="image185" src="http://arapehlivanian.com/wp-content/uploads/2006/05/hooks.jpg" alt="Fish hooks" />One of the defining principles behind the <a href="http://webstandards.org">Web Standards Movement</a> is the separation of structure (HTML), presentation (CSS) and behaviour (DOM Scripting) in a document (web page). Meaning of course that all of your content gets marked up as HTML, everything that has to do with the way that it looks goes into style sheets and any behaviour is handled via DOM Scripting (aka JavaScript). As with any such methodology the three aforementioned layers of separation are nice and neat on paper, but when you get out into the real world of web development it can sometimes get a little messy.
</p>

Case in point, in a recent conversation with [Sarven][1] I was asked whether I thought the `:hover` pseudo-class in CSS belonged to the presentational or behavioural layer. After all, to &#8220;hover&#8221; is to perform an action, and an action is behavioural by it&#8217;s very nature. So why is the `:hover` pseudo-class then found in CSS, the presentational layer? To make things potentially more confusing, using JavaScript you can change the *presentation* of your document via the DOM&#8217;s `style` property collection. So in effect you can affect the document&#8217;s behaviour through the presentational layer and vice versa. This then begs to ask: what belongs where?

<p class="embellished1">
  <img id="image186" src="http://arapehlivanian.com/wp-content/uploads/2006/05/crayons.jpg" alt="Crayons" />Well, let&#8217;s deal with CSS first. After being asked Sarven&#8217;s question I thought about it for a moment and realized that no, in fact, the <code>:hover</code> pseudo-class is not so much a behaviour in and of itself as its a behavioural <em>hook</em> exposed to the presentational layer for the purpose of styling elements that find themselves in a &#8220;hover&#8221; state. In other words, CSS doesn&#8217;t handle the behaviour, the browser does. CSS is simply being allowed&#8211;by the browser&#8211;to style an element that&#8217;s in a hover state.
</p>

<p class="embellished0">
  <img id="image188" src="http://arapehlivanian.com/wp-content/uploads/2006/05/wrench.jpg" alt="A wrench" />Then of course there&#8217;s JavaScript&#8217;s ability to manipulate the document&#8217;s presentation. This is where I believe discretion is necessary. I&#8217;m of the mind that unless absolutely tied into the behaviour, all styling should remain in CSS. For example, rather than toggling an element&#8217;s <code>display</code> attribute value from <code>block</code> to <code>none</code> and back again in JavaScript I prefer to only toggle the element&#8217;s class name. That way I control the presentational aspect of the element in CSS. This keeps both layers as separate as possible by only offering CSS a hook from JavaScript in the form of a class name instead of applying the style rules directly from within JS.
</p>

<p class="embellished0">
  <img id="image187" src="http://arapehlivanian.com/wp-content/uploads/2006/05/thumb.jpg" alt="A hand giving a thumbs up" />So how do you tell when to write style rules directly from the behavioural layer and when not to? My rule of thumb is to only do so when I&#8217;m calculating positions or colours that aren&#8217;t simple predefined states&#8211;like show/hide. In other words, if the user is going to interact with the behavioural layer and cause it to recalculate position or colour values, then those values should be set via JavaScript. Otherwise I try and steer clear of writing entire sets of style rules directly in JavaScript. Doing that just defeats the purpose of good clean code in separate appropriate layers connected simply by hooks.
</p>

 [1]: http://csarven.ca