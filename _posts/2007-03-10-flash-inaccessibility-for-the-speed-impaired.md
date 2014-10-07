---
title: Flash (In)Accessibility for the Speed Impaired
author: Ara Pehlivanian
excerpt: "As if Flash weren't taking enough of a hit on accessibility, a common and easily avoidable practice often employed by Flash designers just makes the case against it all the worse."
layout: post
permalink: /flash-inaccessibility-for-the-speed-impaired/
tags:
  - Accessibility
  - flash
yourls_shorturl:
  - http://a12n.com/2t
---
<p class="embellished0">
  <img src="http://arapehlivanian.com/wp-content/uploads/2007/03/flash-context-menu.gif" alt="Flash Context Menu" />Flash tends to be a taboo when discussing accessibility on the web.
</p>

<del>Mainly because the textual content in a Flash <a href="http://en.wikipedia.org/wiki/Swf"><abbr title="Small Web Format or Shockwave Flash">SWF</abbr></a> file is not accessible to <a href="http://en.wikipedia.org/wiki/Screen_reader">screen readers</a></del>[[*][1]]. It&#8217;s for this reason that the WCAG 1.0 states that [<q cite="http://www.w3.org/TR/WAI-WEBCONTENT/#gl-provide-equivalents">equivalent alternatives to auditory and visual content</q>][2] be provided.

That&#8217;s all well and good for those who have physical impairments, but what about us folks whose computers are the ones that are impaired? My home computer didn&#8217;t fly off of the assembly line last week and isn&#8217;t going to win any performance contests anytime soon. So when I try and access Flash content that&#8217;s a little on the heavy side, I like to be able to right click it and set its quality to &#8220;low&#8221;. That way, I can enjoy the content of the Flash animation without watching it melt down before my very eyes because of a shortfall in processing power. Anti-aliasing a ton of vectors takes a lot of juice.

<p class="embellished1">
  <img src="http://arapehlivanian.com/wp-content/uploads/2007/03/flash-context-menu-disabled.gif" alt="Flash Context Menu (disabled)" />Which brings me to my point. Disabling the Flash context menu is a <strong>bad</strong> idea! By turning it off (actually setting the <code>menu</code> property&#8217;s value to &#8220;<code>false</code>&#8220;), you&#8217;re <em>not only</em> not allowing me to lower the quality of the animation, but you&#8217;re also not allowing people with impaired vision to be able to zoom the content for easier reading. So, though it may be cool, or &#8220;in&#8221; to do it, the next time you&#8217;re tempted to turn off the context menu, do us slower computer owners a big favour and don&#8217;t.
</p>

<p id="update">
  <strong>*Update:</strong> <a href="http://arapehlivanian.com/2007/03/10/flash-inaccessibility-for-the-speed-impaired/#comment-8507">John Dowdell</a> and <a href="http://arapehlivanian.com/2007/03/10/flash-inaccessibility-for-the-speed-impaired/#comment-8509">Tom</a> have brought to my attention that screen readers can in fact access the contents of SWF files. My bad guys.
</p>

 [1]: #update
 [2]: http://www.w3.org/TR/WAI-WEBCONTENT/#gl-provide-equivalents

 *[WCAG]: Web Content Accessibility Guidelines