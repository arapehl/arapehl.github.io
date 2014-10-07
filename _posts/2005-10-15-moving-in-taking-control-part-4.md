---
title: 'Moving in: Taking control (Part 4)'
author: Ara Pehlivanian
layout: post
permalink: /moving-in-taking-control-part-4/
tags:
  - css
  - moving in
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/7r
categories:
  - General
---
As you may have noticed, I had a little bit of a [design crisis][1] a few days ago. As a result I&#8217;ve decided to go ahead and work on the XHTML and CSS layout of the site first. I have a general ideal of where I&#8217;d like to take the markup and layout so I figure I&#8217;ll get that done first.

Currently I&#8217;m using the famous out-of-the-box [Kubrick][2] template. As nice as it is, it isn&#8217;t for me. I have very specific requirements that I can&#8217;t realize with someone else&#8217;s template. For example, I want a fluid grid with horizontal navigation up top and three columns. I also want to be able to put a lot of the content that&#8217;s currently in the sidebar into separate, dedicated pages. You can see that I&#8217;ve taken the first step by creating the pages. That already required a little [WordPress lesson][3]. Oh did I mention I&#8217;m learning PHP and WordPress as I go?

Maybe it&#8217;s time to clarify my experience (as a little aside). I know the following: HTML, XHTML, CSS, the DOM, JavaScript, XML, XSLT, ASP(VB Script), ASP.NET(C#), some SQL and an assortment of other related technologies which I can&#8217;t remember off the top of my head. Unfortunately PHP isn&#8217;t one of them, though it soon will be. ;-)

So where was I? Oh yeah, in my upcoming template I&#8217;ve cleaned up the auto-discovery feed links (I&#8217;m using FeedBurner&#8217;s SmartFeed&trade; to translate feed types on-the-fly) and I&#8217;ve moved the navigation links to the upper part of the page. Unfortunately I had to do away with the `<a href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages()</a>` function because it didn&#8217;t allow me to place the site&#8217;s home link within its generated list (more on this in a future post). So the nav items will be hand coded.

Otherwise, things are going frustratingly slowly but smoothly. I&#8217;ll be reporting on my progress periodically as I go. Oh and as for the post slugs, I haven&#8217;t quite decided how I want to handle them so in the meanwhile &#8220;sorry [Mathias][4].&#8221; ;-)

 [1]: http://arapehlivanian.com/2005/10/11/moving-in-the-mid-design-crisis/
 [2]: http://binarybonsai.com/kubrick/
 [3]: http://codex.wordpress.org/Creating_an_Archive_Index
 [4]: http://arapehlivanian.com/2005/10/06/proper-uri-design/#comment-14