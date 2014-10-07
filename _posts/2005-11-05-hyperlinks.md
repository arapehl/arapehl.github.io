---
title: Do you know how to write a hyperlink correctly? You might be surprised.
author: Ara Pehlivanian
layout: post
permalink: /hyperlinks/
tags:
  - explanations
  - search
  - semantics
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/1j
categories:
  - General
---
I recently covered [proper URI design][1] after which I was rightly [chastised][2] for not following my own advice. Now I&#8217;d like to cover their correct implementation via hyperlinks. Knowing how to correctly create hyperlinks is very important for several reasons, not the least of which being that hyperlinks are the most basic and foundational component of the web.

<blockquote cite="http://www.w3.org/People/Berners-Lee/Longer.html">
  <p>
    &#8220;In 1989, [<a href="http://www.w3.org/People/Berners-Lee/">Tim Berners-Lee</a>] proposed a global hypertext project, to be known as the World Wide Web. Based on the earlier &#8216;<a href="http://www.w3.org/History/1980/Enquire/">Enquire</a>&#8216; work, it was designed to allow people to work together by combining their knowledge in a web of hypertext documents.&#8221;&#8211;<cite><a href="http://www.w3.org/People/Berners-Lee/Longer.html">Longer Bio for Tim Berners-Lee</a></cite>
  </p>
</blockquote>

<!-- wp_ad_camp_1 -->

In keeping with my [case for semantics][3] I&#8217;d like to re-iterate that everything you type has a meaning—rather *should* have a meaning. So for example, in order to signal the end of a sentence, I&#8217;ll use the period character. Or if I want to signal a break in my line of thought, I&#8217;ll use the [em dash][4] character. Likewise, when I want to point a reader to a document on the web, I do it with a hyperlink. But in order to avoid confusion, I need to make sure that I do it right. Because, just as the misuse of punctuation and grammar can cause confusion, so can the misuse of markup. How often have you seen the <q cite="http://www.google.com/search?hl=en&lr=&safe=active&q=click+here"><a rel="nofollow" href="http://www.google.com/search?hl=en&lr=&safe=active&q=click+here">click here</a></q> hyperlink? It&#8217;s everywhere, and it&#8217;s the worst thing you can do. Let me explain. Take the following example:

    <a href="http://arapehlivanian.com">
        Ara Pehlivanian
    </a>

Semantically speaking, the example above denotes the following: create an [anchor][5] pointing to arapehlivanian.com and describe it with the following hypertext: &#8220;Ara Pehlivanian.&#8221; It doesn&#8217;t make much sense to describe a hyperlink using text that is in no way related to its hypertext reference (or `href` attribute), does it? Besides, well-written hyperlinks are a must when it comes to non-conventional devices such as screen readers that rely on a hyperlink&#8217;s hypertext for descriptive purposes. It&#8217;s also becomes important when your links are—for whatever reason—pulled out of context. If all you used as hypertext was the word &#8220;here,&#8221; imagine what a list of your links would look like. Reading it would make no sense at all.

Then of course there are search engines who regularly crawl and index the web. Whenever they encounter a hyperlink, they associate its hypertext with its hypertext reference. If the hypertext for the hyperlink doesn&#8217;t adequately describe its hypertext reference, you get strange results such as the now infamous &#8220;<a rel="nofollow" href="http://www.google.com/search?q=failure">failure</a>&#8221; [GoogleBomb][6]. And though things like that may be mildly amusing, they certainly don&#8217;t help your search ranking.

You may need to rethink the way that you write copy in order to implement well-written hyperlinks, but believe me, the effort is well worth it.

 [1]: /2005/10/06/proper-uri-design/
 [2]: /2005/10/06/proper-uri-design/#comment-14
 [3]: /2005/10/20/the-case-for-semantics/
 [4]: /2005/10/19/em-dash-explained/
 [5]: http://htmlhelp.com/reference/html40/special/a.html
 [6]: http://www.answers.com/googlebomb