---
title: Be Lazy, Let the Browser Do the Work for You
author: Ara Pehlivanian
layout: post
permalink: /be-lazy-let-the-browser-do-the-work-for-you/
tags:
  - browser
  - cascade
  - css
  - lazy
  - standards
  - web dev
  - web development
yourls_shorturl:
  - http://a12n.com/4v
categories:
  - General
---
Imagine you work for a company that has an online product catalog and that your job is to maintain the product images. Now imagine your boss comes to you and says, &#8220;here&#8217;s a list of a thousand products that need to have &#8216;40% off&#8217; put on them, and we need it for tomorrow, noon.&#8221; So you work all night only to have him come to you in the morning and say, &#8220;did I say forty? I meant fifty.&#8221; Now you&#8217;ve got till noon to update a thousand images, go! The more efficient way to handle that situation would be to have a macro, or a template, or some other automated way to either update those images or just superimpose the discount on each of those images.

The moral of the story is, work smarter not harder. When a computer can do the work for you, let it. There&#8217;s no glory in doing it yourself. This same moral can be transposed to front-end web development. 

There is this thing called &#8220;flow&#8221; in the browser environment. Think of it as a really crude physics engine. All of the elements rendered in a page are initially a part of the document&#8217;s flow. When an image within the flow is enlarged, the text adjacent to it gets shoved over. When it&#8217;s reduced, the text is drawn closer. This is good because you don&#8217;t need to worry about positioning the text when playing with the size of an image. It&#8217;s handled automatically by the browser.

Now imagine if you were to break the flow and opt to position everything yourself. Maintenance would become a nightmare. Sadly this often happens when people get their hands on CSS and don&#8217;t know how to properly leverage it. Instead of letting the browser handle the positioning of the elements and just *nudging* them in place with a few strategically placed rules, they opt to brute force everything into position. Of course, what happens when an image size changes? or a bit of text goes longer than anticipated? Everything breaks. Then they&#8217;re up all night fixing a ton of style sheets.

The thing to remember with CSS is: less is more. Really, the [cascade][1] works best in conjunction with document flow. Restraining either too much defeats the purpose and leads inevitably to unnecessary headaches.

 [1]: http://arapehlivanian.com/2008/04/10/the-c-in-css-stands-for-cascade/