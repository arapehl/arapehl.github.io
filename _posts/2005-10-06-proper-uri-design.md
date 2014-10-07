---
title: Proper URI design
author: Ara Pehlivanian
layout: post
permalink: /proper-uri-design/
tags:
  - architecture
  - Articles
  - web development
yourls_shorturl:
  - http://a12n.com/14
categories:
  - General
---
Can your site&#8217;s pages be accessed without their file extensions? Do your pages have a ton of querystring parameters trailing after them? Are your pages organized by author or subject name? How much thought do you put into the creation of your URIs? A lot? A little? What&#8217;s a [URI][1] you ask?

Believe it or not, a lot of thought goes into a seemingly simple URI. In fact, the simpler it is, the more thought it takes. Especially if you&#8217;re hoping to make your content available for years, and years, and years to come. That&#8217;s right, proper URI design helps in their longevity because we won&#8217;t feel the need to move or abandon files or entire folder hierarchies later on down the line when our sites grow in new and different directions. But &#8220;Ara,&#8221; you say. &#8220;It&#8217;s normal. My site grows, times change, what I put up two years ago is no longer relevant.&#8221; Wrong! URIs should last forever. The rule of thumb is: <q cite="http://www.answers.com/topic/link-rot#wp-Combating_Link_Rot">Do not keep a hyperlink collection unless you are willing to look after it.</q> &#8220;You&#8217;re nuts,&#8221; you say. &#8220;Sometimes it&#8217;s inevitable. Its time comes and the content&#8217;s gotta go!&#8221; Okay, that&#8217;s fine. But there *are* ways of dealing with the [removal of old content][2] too, and it isn&#8217;t to just delete the files.

> Designing [URIs] mostly means leaving information out.

With a little forethought, we won&#8217;t ever have to delete files. The problem is, we don&#8217;t take the long view when placing content. How often have you stopped and wondered if the folders you&#8217;re creating will make sense three years from now? Will `/team/robert/uri-tips.html` be valid once Robert leaves the team? Or what happens to `/betas/cool-widget.html` when Cool Widget comes out of beta? By moving the file, have you just inadvertently created link rot? What will happen when those who have bookmarked your Cool Widget page come back and get an &#8220;Error 404: Page Not Found&#8221; message? Will they start looking around to try and find Cool Widget elsewhere on your site? Or will they leave your site disappointed, having lost confidence in you? Because of consequences like this, I believe that proper URI design should just be another part of the web developer&#8217;s skill set.

### Recommended Reading

*   [W3C: Managing URIs][3]
*   [W3C: Cool URIs don&#8217;t change][4]
*   [Jakob Nielsen: URLs as UI][5]
*   [Answers.com: Link Rot][6]

 [1]: http://www.w3.org/Addressing/
 [2]: http://diveintomark.org/archives/2003/03/27/http_error_410_gone
 [3]: http://www.w3.org/QA/Tips/uri-manage
 [4]: http://w3.org/Provider/Style/URI
 [5]: http://www.useit.com/alertbox/990321.html
 [6]: http://www.answers.com/topic/link-rot