---
title: And now for a little progressive enhancement
author: Ara Pehlivanian
excerpt: I reworked my feeds page to incorporate some relatively advanced CSS features that are only supported by modern browsers such as Firefox. Likewise the post contains some advanced CSS functionality itself.
layout: post
permalink: /and-now-for-a-little-progressive-enhancement/
autometa:
  - advanced-css advanced-css-tutorial cross-browser cross-browser-css cross-browser css-advanced css-style-sheets graceful-degradability progressive-enhancement
tags:
  - css
  - standards
  - web development
yourls_shorturl:
  - http://a12n.com/2y
categories:
  - General
---
So I finally got around to working on my [feeds][1] page. It wasn&#8217;t very impressive as you can see in the screen cap below.

<div class="figures">
  <div class="figure">
    <a href="http://arapehlivanian.com/wp-content/uploads/2006/04/old_feeds.jpg" title="Screen capture of old feeds page"><img id="image158" src="http://arapehlivanian.com/wp-content/uploads/2006/04/old_feeds.thumbnail.jpg" alt="Screen capture of old feeds page" /></a> <p class="caption">
      Old feeds page
    </p>
  </div>
  
  <p>
    At first I had a hard time trying to figure out how to accommodate so many feed chicklets. I have 5 feeds times 8 chicklets each, that comes out to 40 little images that needed to be laid out in such a way so as not to look so busy. (<em>Even more have been added since the writing of this post. At last count we&#8217;re up to 60 chicklets.</em>) I finally came up with the current solution as illustrated in the screen caps below.
  </p>
  
  <div class="figures">
    <div class="figure">
      <a href="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ie.jpg" title="Screen capture of new feeds page in IE"><img id="image159" src="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ie.thumbnail.jpg" alt="Screen capture of new feeds page in IE" /></a> <p class="caption">
        New feeds page in IE
      </p>
    </div>
    
    <div class="figure">
      <a href="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ff.jpg" title="Screen capture of new feeds page in Firefox"><img id="image160" src="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ff.thumbnail.jpg" alt="Screen capture of new feeds page in Firefox" /></a> <p class="caption">
        New feeds page in Firefox
      </p>
    </div>
    
    <div class="figure">
      <a href="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ff2.jpg" title="Screen capture of new feeds page in Firefox with one feed panel expanded"><img id="image161" src="http://arapehlivanian.com/wp-content/uploads/2006/04/new_feeds_ff2.thumbnail.jpg" alt="Screen capture of new feeds page in Firefox with one feed panel expanded" /></a> <p class="caption">
        New feeds page in Firefox with one feed panel expanded
      </p>
    </div>
  </div>
</div>

You&#8217;ll notice that one version has all the feed chicklets visible, that&#8217;s in IE. Firefox on the other hand has only the little orange XML icon visible and gives you the rest once you hover over it. Now I used the term *progressive enhancement* in this post&#8217;s title because&#8211;like this site&#8217;s rounded corners you only see in Firefox&#8211;you&#8217;re able to experience the show/hide functionality in Firefox due to its more comprehensive support of CSS2 (granted the rounded corners are a proprietary Mozilla feature but who&#8217;s going to wait around for CSS3? ;-). In other words, the better the browser the nicer the experience.

**For bonus points** try and find a &#8220;progressive enhancement&#8221; feature in this very post!

 [1]: /syndication/