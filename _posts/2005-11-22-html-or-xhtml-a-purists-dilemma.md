---
title: 'HTML or XHTML: A purist&#8217;s dilemma'
author: Ara Pehlivanian
excerpt: Ara grapples with the question of whether he should abandon XHTML in favour of HTML in light of some recent revelations.
layout: post
permalink: /html-or-xhtml-a-purists-dilemma/
tags:
  - Articles
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/5w
categories:
  - General
---
Whenever possible, I like to do things the right way. Proper implementation of anything&#8212;though it may take more effort initially&#8212;returns dividends in the form of higher performance, reliability, scalability, re-usability, and so on and so forth. This principle applies to life in general and isn&#8217;t limited to web development (read: [Tacoma Narrows Bridge][1]). It is however at the core of this article and the focus of the issue I am wrestling with.

For some time now, I was under the impression that XHTML was simply &#8220;better HTML,&#8221; due to its inherent well formedness&#8212;what with it being written in XML and all. But it seems I was mistaken ([and I&#8217;m willing to admit it][2]). Recently I&#8217;ve been reading articles by [Anne van Kesteren][3], and it&#8217;s gotten me wondering if I didn&#8217;t just jump on the XHTML bandwagon without even asking myself that one all-important question: &#8220;Do I really need this?&#8221; Had I taken the time to explore the issue a little, I would have found out that in order to deliver XHTML to a client properly, I should be doing it via the `application/xhtml+xml` MIME type. Currently my documents are delivered as `text/html`, so all I have to do is change the MIME type right? Not really. While Firefox supports it, IE doesn&#8217;t. A document delivered to IE using the `application/xhtml+xml` MIME type causes the browser to display a download window as it doesn&#8217;t support it as a known document format. I could rig my web server to deliver the document in `text/html` for IE, but then I&#8217;d have to ask myself: &#8220;Is the effort worth it?&#8221; In other words, what advantage would XHTML bring me for the effort I&#8217;d have to expend in properly implementing it? Not to mention the fact that it would still be delivered in the incorrect MIME type in IE. The answer unfortunately is: none. Though there really aren&#8217;t any major semantic differences between HTML and XHTML, I&#8217;d really only need to use the latter if I had to extend HTML with MathML or some other custom markup languages. For more on this, read Anne&#8217;s post entitled: &#8220;[MIME types matter; DOCTYPEs don&#8217;t][4]&#8220;

Now, some of you may be thinking &#8220;big deal, it still validates as XHTML even if the MIME type says it&#8217;s HTML and not XHTML.&#8221; Well, that would be a bad assumption to make since according to the W3C HTML WG Chair [Steve Pemberton][5], <q cite="http://lists.w3.org/Archives/Public/www-html/2000Sep/0024.html"><a href="http://lists.w3.org/Archives/Public/www-html/2000Sep/0024.html">&#8230;documents served as text/html should be treated as HTML and not as XHTML.</a></q> This means that even though I work very hard at writing properly formed XHTML, in reality what I&#8217;ve been doing is exactly what I&#8217;ve been trying hard to avoid: I&#8217;ve been writing tag soup! That&#8217;s right, since in essence I&#8217;ve been delivering HTML documents using mal-formed HTML.

My dilemma is the following: Do I switch to HTML 4.01 and get used to uppercase tags that don&#8217;t self-close? Do I stay with XHTML 1.0 Strict and keep delivering it with the incorrect MIME type? Do I rig Apache to deliver my XHTML with the `application/xhtml+xml` MIME type and abandon visitors with older browsers (like IE 6). Or do I find a happy medium that delivers `application/xhtml+xml` to conforming browsers and `text/html` to everyone else?

What do you think?

### Related Reading

*   [XHTML advocates considered erroneous][6] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [MIME types matter; DOCTYPEs don&#8217;t][4] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [Why MIME types are not like handing someone a cup of coffee saying it’s hot chocolate][7] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [Well-Formed][8] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [Markover: limpid.nl][9] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [XHTML is invalid HTML][10] by <cite><a href="http://annevankesteren.nl/about">Anne van Kesteren</a></cite>
*   [Re: Sniffing XHTML sent as text/html][11] by <cite><a href="http://www.cwi.nl/~steven/">Steven Pemberton</a></cite>
*   [xhtml v. html: a tiresome debate][12] by <cite><a href="http://molly.com/about.php">Molly E. Holzschlag</a></cite>

 [1]: http://www.answers.com/Tacoma%20Narrows%20Bridge
 [2]: http://www.molly.com/2005/11/14/web-standards-and-the-new-professionalism/
 [3]: http://annevankesteren.nl/about
 [4]: http://annevankesteren.nl/2004/07/mime
 [5]: http://www.w3.org/People/all#steven
 [6]: http://annevankesteren.nl/2005/11/xhtml-advocates
 [7]: http://annevankesteren.nl/2005/04/mime-types
 [8]: http://annevankesteren.nl/2004/06/well-formed
 [9]: http://annevankesteren.nl/2004/07/limpid
 [10]: http://annevankesteren.nl/2004/06/invalid-html
 [11]: http://lists.w3.org/Archives/Public/www-html/2000Sep/0024.html
 [12]: http://www.molly.com/2004/07/23/xhtml-v-html-a-tiresome-debate/