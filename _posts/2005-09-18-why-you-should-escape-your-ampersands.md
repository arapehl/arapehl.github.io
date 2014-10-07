---
title: Why you should escape your ampersands
author: Ara Pehlivanian
layout: post
permalink: /why-you-should-escape-your-ampersands/
tags:
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/57
categories:
  - General
---
[Molly][1]&#8216;s recent [Searching for Standards][2], mentions that AOL&#8217;s search engine doesn&#8217;t validate due to unescaped ampersands. I&#8217;ve [personally seen][3] a lot of this happening and I thought I&#8217;d relate a little experience I had a few years ago while working for my [previous employer][4] where I learned the hard way that I should escape my ampersands.

The project called for a set of parameters to be passed through the querystring, one of which was named &#8220;sect&#8221; which was short for the word &#8220;section.&#8221; The final URI looked something like this:

`<a href="http://www.domain.com/page.asp?param=1&sect=2">My Link</a>`

Much to my surprise, the link didn&#8217;t work. Instead it would render something like this:

`<a href="http://www.domain.com/page.asp?param=1&sect;=2">My Link</a>`

A little investigation and I discovered that &sect (or more properly &sect;) was actually the [character entity][5] for the section sign. So when the browser came across my anchor it took the contents of the `href` attribute and did what it was supposed to do. It parsed its contents, found character entities and rendered them. Of course, by rendering the `&sect` portion of my querystring, it broke my anchor.

Now, that&#8217;s one real world example of how not escaping your ampersands can cause you trouble. Though you may be thinking &#8220;yeah, but what if I don&#8217;t use the word *sect* in my querystrings?&#8221; Well consider this. There are many more character entities that can pose a danger to your code. What if you were passing currency information using any of the following entities: &cent;, &yen; or &pound;? Or what if you wanted to use something like: &not;?

The bottom line is, if you don&#8217;t escape your ampersands, you could end up with broken code.

 [1]: http://www.molly.com
 [2]: http://www.molly.com/2005/09/08/searching-for-standards/
 [3]: http://thesimpleweb.blogspot.com/2005/09/new-gapcom-peak-under-hood.html
 [4]: http://www.justforlaughs.com/
 [5]: http://www.htmlhelp.com/reference/html40/entities/latin1.html