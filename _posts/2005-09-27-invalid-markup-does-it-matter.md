---
title: 'Invalid markup: does it matter?'
author: Ara Pehlivanian
layout: post
permalink: /invalid-markup-does-it-matter/
tags:
  - semantics
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/1l
categories:
  - General
---
Don&#8217;t get me wrong. If you know me, you know that I&#8217;m the first one to push for valid markup. I&#8217;m a perfectionist at heart, and nothing pleases me more than seeing that beautiful message on the [W3C&#8217;s Validator][1]: &#8220;This page is Valid XHTML 1.0 Strict!&#8221; But the more I think about it and the more I talk to people about it, the less I see a *need* for it. Yes, I know, it ensures accessibility, it ensures compatibility across multiple platforms, it&#8217;s machine readable and it follows all the rules, but so long as the mainstream browsers don&#8217;t stop accommodating bad markup, what&#8217;s the point?

I wish there were a more solid reason for conformity. Like, say for example, if the browser behaved like a compiler. Rather than doing its best to patch up faulty markup, what if it spat out a list of errors that need correcting. Then maybe people would make more of an effort. Or if the server simply refused to serve up documents that didn&#8217;t validate. But as things are right now, there&#8217;s no real incentive to make sure all of your tags are closed and all of your ampersands are escaped. The worst of it is when a document is declared to be XHTML, no matter the flavour, and doesn&#8217;t validate, but the browser* still parses it! I mean, isn&#8217;t XHTML <q cite="http://www.w3.org/TR/xhtml1/#xhtml"><a href="http://www.w3.org/TR/xhtml1/#xhtml">a reformulation of HTML 4 in XML 1.0</a></q>? And isn&#8217;t XML unforgiving to the point that an [XML parser must stop if it reaches a fatal error][2]?

So I ask you, what&#8217;s the deal? We fight for standards, we expend all this energy, and yet the major browsers in use today could care less if the document they&#8217;re parsing is well formed. How are we supposed to be taken seriously as professionals if as far, as the browser&#8217;s concerned, tag soup is as good as a valid document?

I say let&#8217;s start a movement, &#8220;a zero tolerance for invalid markup&#8221; campaign of sorts. Let&#8217;s really [take back the web][3], let&#8217;s [browse happier][4]. Any takers?

*\* I don&#8217;t specify browsers by name because all of the popular ones are equally guilty.*

 [1]: http://validator.w3.org/
 [2]: http://www.w3.org/TR/2004/REC-xml-20040204/#dt-fatal
 [3]: http://www.spreadfirefox.com/
 [4]: http://browsehappy.com/
