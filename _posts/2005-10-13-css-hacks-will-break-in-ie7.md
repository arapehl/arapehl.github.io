---
title: CSS hacks will break in IE7!
author: Ara Pehlivanian
layout: post
permalink: /css-hacks-will-break-in-ie7/
tags:
  - css
  - hacks
  - news
  - standards
  - web development
yourls_shorturl:
  - http://a12n.com/4f
categories:
  - General
---
It&#8217;s official. Among the [new functionality][1] introduced in IE7 are many parser bug fixes. That means that [several CSS hacks will fail][2] as a result.

Included in those that will break are the following hacks:

*   [html > body][3]
*   [* html][4]
*   [head:first-child + body][5]
*   [head + body][6]
*   [body > element][3]

All is not lost however. The recommended workaround is to use [conditional comments][7].

 [1]: https://blogs.msdn.com/ie/archive/2005/07/29/445242.aspx
 [2]: http://blogs.msdn.com/ie/archive/2005/10/12/480242.aspx
 [3]: http://css-discuss.incutio.com/?page=ChildHack
 [4]: http://css-discuss.incutio.com/?page=StarHtmlHack
 [5]: http://centricle.com/ref/css/filters/tests/owen/
 [6]: http://www.dithered.com/css_filters/css_only/head_adjacent_sibling_body.html
 [7]: http://msdn.microsoft.com/library/default.asp?url=/workshop/author/dhtml/overview/ccomment_ovw.asp