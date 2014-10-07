---
title: Microformats, English only?
author: Ara Pehlivanian
excerpt: Experiencing the Microformats growing pains first hand
layout: post
permalink: /microformats-english-only/
tags:
  - microformats
  - standards
yourls_shorturl:
  - http://a12n.com/1d
categories:
  - General
---
Microformats, for those who aren&#8217;t in the know, are simply a way to further add semantics to HTML content by using agreed upon class names based on existing models already in use elsewhere. One of the most common microformats&#8211;and the subject of this post&#8211;is [hCard][1], which is based upon the widely used vCard ([RFC 2426][2]) format.

I&#8217;ve had the (dis)pleasure of trying to implement hCard on two bilingual sites now only to come to the conclusion that hCard probably wasn&#8217;t as well thought out&#8211;or to be fair, mature&#8211;as I&#8217;d have hoped. The reason for it can be seen clearly in the following code example:

<pre>&lt;div class="vcard"&gt;
  &lt;span class="tel"&gt;T&eacute;l.:&lt;span class="value"&gt;+1.514.555.1212&lt;/span&gt;&lt;/span&gt;
  &lt;span class="tel"&gt;&lt;span class="type"&gt;Fax&lt;/span&gt; T&eacute;l&eacute;c.:&lt;span class="value"&gt;+1.514.555.1212&lt;/span&gt;&lt;/span&gt;
&lt;/div&gt;</pre>

The telephone number&#8217;s `type` value is derived from the span tag&#8217;s contents which is displayed in the clear. It is therefore a part of the page&#8217;s contents and difficult, if not impossible to justify in a page whose contents are in French&#8211;or Spanish, or whatever. Of course, one could always hide the text with CSS, but that&#8217;s hardly a solution when separation of content and presentation is concerned.

[I raised the issue][3] on the Microformats discussion list and was given a solution that seemed to make sense to me. But shortly thereafter it was pointed out by someone else that the solution *itself* was a [documented issue][4] and not a good solution after all.

In the midst of all of this I came to realize that though Microformats are a great idea and highly useful when they work, the broader issue of internationalization needs to be worked into them if they&#8217;re truly to become useful outside of the &#8220;English only&#8221; world.

 [1]: http://microformats.org/wiki/hcard
 [2]: http://www.ietf.org/rfc/rfc2426.txt
 [3]: http://microformats.org/discuss/mail/microformats-discuss/2007-March/009000.html
 [4]: http://microformats.org/wiki/hcard-issues