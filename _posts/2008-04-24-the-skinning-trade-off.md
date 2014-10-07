---
title: The Skinning Trade-off
author: Ara Pehlivanian
layout: post
permalink: /the-skinning-trade-off/
yourls_shorturl:
  - http://a12n.com/1o
categories:
  - General
tags:
  - button
  - checkbox
  - dropdown
  - element
  - form
  - input
  - pulldown
  - radio button
  - select box
  - skin
  - style
  - text field
  - web development
---
Anyone who&#8217;s built a website has likely had to deal with the temptation to skin [native browser elements][1], such as the pulldown menu, the input field, the radio button, the checkbox, the button, the text field and the scroll bar. The most common skinning job that pervades the web is that of the simple button. That&#8217;s because of the styling latitude browsers allow for that particular element. However, apart from a few colour changes, styling a pulldown, or worse a scroll bar, is next to impossible.

Even though browsers don&#8217;t allow elements to be skinned, it&#8217;s still possible to emulate them in JavaScript and skin them that way. But there&#8217;s a problem with this. Whenever you emulate a browser&#8217;s native functionality, you inevitably lose something. That&#8217;s because native elements have a whole slew of unseen things built into them that come for free. Some examples of this include `focus` and `blur` events, the ability to tab to them, that pressing the enter key while focused will in most cases trigger the element&#8217;s onclick event, and that changes to the state of some elements will be directly communicated to the OS  for use by assistive technologies. Emulating these things is at best a difficult and cumbersome task and at worst, impossible.

On top of it all, usability experts recommend leaving these elements in their native rendering because that&#8217;s what users are used to and are expecting. Changing the appearance of an otherwise familiar element can cause confusion and will most likely cause users to [think][2]<img src="http://www.assoc-amazon.ca/e/ir?t=arapehli-20&#038;l=as2&#038;o=15&#038;a=0321344758" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />, which isn&#8217;t a good idea.

So even though skinning a browser element gets you all sorts of graphical awesome, you&#8217;re going to inevitably lose something by doing it. So the next time you&#8217;re tempted to skin a browser element, think twice and maybe just leave it alone, for all our sakes.

 [1]: http://www.designerstoolbox.com/designresources/elements/
 [2]: http://www.amazon.ca/gp/product/0321344758?ie=UTF8&#038;tag=arapehli-20&#038;linkCode=as2&#038;camp=15121&#038;creative=330641&#038;creativeASIN=0321344758

 *[OS ]: Operating System