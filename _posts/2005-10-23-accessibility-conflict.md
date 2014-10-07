---
title: Accessibility Conflict
author: Ara Pehlivanian
layout: post
permalink: /accessibility-conflict/
tags:
  - Accessibility
  - web development
yourls_shorturl:
  - http://a12n.com/4z
categories:
  - General
---
I don&#8217;t know about you, but in the interest of saving time and just plain avoiding the unnecessary use of my mouse, I&#8217;ve come to learn a few shortcut keys for when I browse the web. Luckily the one I use most frequently&#8212;<kbd>Alt</kbd>+<kbd>D</kbd>, used to access the address bar&#8212;works in both IE and Firefox (my browser of choice).

Now, I&#8217;m all for accessibility and [access keys][1] but it gets a little annoying when a technology meant to help becomes a hindrance. Case in point, I was on the [Opera Website][2] and wanted to type in a different address in the address bar so I hit <kbd>Alt</kbd>+<kbd>D</kbd> and much to my chagrin, ended up on the Opera Download page before I could even type anything else. It took me half a second to realize that this happened because the access key assigned to the Download Menu Item was the letter D. And of course, since access keys in Firefox (and IE) are accessed by pressing the <kbd>Alt</kbd> key with the assigned letter, <kbd>Alt</kbd>+<kbd>D</kbd> brought me to the Download page instead of the Firefox address bar.

My point is this: I see the web as a medium for the transmission of semantically marked up information meant for platform independent consumption. Accessibility plays a very important part in the notion of it being platform independent and therefore the technology of access keys is definitely valid and essential. So if the web is platform independent then it stands to reason that the assignation of the access key &#8220;D&#8221;, though it conflicts with IE and Firefox shortcut keys, is completely legal and should remain unchanged. It is therefore the browser&#8217;s responsibility to make sure that it doesn&#8217;t break down in situations where a certain functionality overrides its internal key mapping.

What do you think?

 [1]: http://www.alistapart.com/articles/accesskeys/
 [2]: http://opera.com