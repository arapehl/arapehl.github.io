---
title: 'Targeting Browsers, Why It&#8217;s a Good Idea'
author: Ara Pehlivanian
excerpt: |
  |
    
    Gone are the days where you need a message like, “This site is best viewed with Netscape 4” on the front page of your site, right? Well maybe, then again maybe not.
layout: post
permalink: /targeting-browsers-why-its-a-good-idea/
yourls_shorturl:
  - http://a12n.com/38
categories:
  - General
tags:
  - browsers
  - demographics
  - standards
  - study
  - target
  - web development
---
Gone are the days where you need a message like, “This site is best viewed with Netscape 4” on the front page of your site, right? Well maybe, then again maybe not.

Though you don’t need the message anymore, the idea of targeting specific browsers isn’t such a terrible idea. I know, the purists in the crowd are already chomping at the bit to flame me in the comments. Hear me out. I too am a purist at heart. I’m all for cross-browser compatibility, graceful degradation, progressive enhancement and progressive enrichment. But I also believe that a lot can be gained in knowing what browser(s) you’re building your site for. In other words, a study in visitor demographics should be a fundamental step in any site’s planning process. If the project is a site redesign, then a good look at the site’s logs is warranted. If however, the site is to be built from scratch, then a study of the kind of the site’s target demographic is advised.

Why bother with all of this? After all, shouldn’t all sites work on all browsers? Yes, but when you get into the realm of progressive enhancement, it would be nice to know to what lengths you can or should bother to enhance a site. In other words, it’s good to know where to focus your efforts. After all, it isn’t often that you’ll find yourself with limitless budget and time to deliver on a project. Often times you’ll be faced with deadlines and budget constraints and knowing where to devote the bulk of your energy would help in delivering on time and on budget.

I’m willing to bet that if you were to look at the visitor logs of a site like xkcd.com and compare them to those of yahoo.com, you’d see vastly different numbers for visitors who use IE6. That’s because Yahoo caters to a larger swath of the general public whereas XKCD is a comic targeted primarily at geeks. Geeks are well known to regularly update their browsers and are also known to run from Internet Explorer like it was the second coming of the black plague.

So what are some examples of targeting browser behaviour? Well take IE6’s infamous lack of PNG-24 alpha support (that’s where IE6 shows a solid gray rather than transparency in files saved in the PNG-24 format). If you see that a large enough number of visitors to your site are using IE6, you should go the extra mile and rig one of the many patches available to fix the issue. However, since those patches often take time and are cumbersome to set up (to say nothing of the maintenance headache they create), you could also get away with not doing it on sites where the majority of visitors don’t use IE6.

Bottom line, if you&#8217;ve got the time and budget to go all out and make your site work perfectly on all browsers, good on ya. But if you don&#8217;t then a small study of browser demographics would be a good idea.