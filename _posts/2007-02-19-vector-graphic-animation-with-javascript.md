---
title: Vector graphic animation with JavaScript
author: Ara Pehlivanian
excerpt: My starfield grows up
layout: post
permalink: /vector-graphic-animation-with-javascript/
tags:
  - canvas
  - web development
yourls_shorturl:
  - http://a12n.com/4r
categories:
  - General
---
<p class="embellished0">
  <img src="http://arapehlivanian.com/wp-content/uploads/2007/02/starfield.jpg" alt="Starfield screenshot" />So my <a href="http://arapehlivanian.com/wp-content/uploads/2007/02/canvas.html">starfield</a>* has evolved a little. I improved the math that I was using to plot the stars and I added the following improvements:
</p>

*   Shape support! Any shape you want can be passed via an array of JSON vector coordinate objects
*   Independent X and Y sine wave applied to star motion
*   Depth shading for added realism
*   Ability to hide shameless plug message :-)
*   Ability to stop/start the animation
*   Plus a bunch of other params I haven&#8217;t exposed yet through the UI

Am I taking myself too seriously? Yeah, maybe a little, but I find this kind of thing fun and who knows, it could eventually prove useful. But don&#8217;t let me get ahead of myself. For now, playing with stars is fun.

Oh, and don&#8217;t knock the buttons code in the page, I just threw those in there real quick to be able to give control over the starfield object. I didn&#8217;t feel like going nuts with the code&#8217;s cleanliness (that&#8217;s in the actual canvas.js file ;)

<small>*This demo requires Safari or Firefox 1.5+ to work.</small>