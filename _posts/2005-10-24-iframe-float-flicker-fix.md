---
title: (AdSense) Iframe float flicker fix
author: Ara Pehlivanian
layout: post
permalink: /iframe-float-flicker-fix/
tags:
  - css
  - standards
  - web development
yourls_shorturl:
  - http://a12n.com/6n
categories:
  - General
---
<ins datetime="2005-11-30T15:49:06+00:00"><strong>Update: </strong>Looks like <a href="http://mozilla.com">Firefox 1.5</a> no longer suffers from the bug so go upgrade now!!</ins>

<ins datetime="2005-10-28T16:23:38-05:00"><strong>Update:</strong> This solution may not work as advertised. I ended up not using it in my own project. Watch this space for the solution I did use.</ins>

Up until a few days ago I thought that this bug was unique to the project I was working on. For reasons that are beyond the scope of this post, I needed to float a div containing an iframe. The problem was that, due to a bug in Firefox&#8217;s rendering engine, there would be a brief flicker where the iframe would appear in the far left of the screen while the rendering engine decided what content went around the floated div. To make matters worse, I needed to animate&#8212;expand/retract&#8212;the div in question. As a result, every frame of the animation would cause the iframe to flicker. That of course was unbearable and unacceptable.

Now, I say <q cite="http://arapehlivanian.com/2005/10/24/iframe-float-flicker-fix/">up until a few days ago</q> because I recently realized that this problem plagued anyone who floated Google&#8217;s AdSense ads, since they too are contained in an iframe.

Well, if you&#8217;ve been dying for a solution, here it is:

<!--more-->

### Code Sample

    
    <style type="text/css">
    div
    {
      float: left;
    }
    #parent
    {
      display: table;
    }
    #child
    {
      float: none;
      display: table-cell;
    }
    </style>
    
    <div id="parent">
      <div id="content">
        <p>content content content ...</p>
        <p>content content content ...</p>
        <p>content content content ...</p>
      </div>
      <div id="child">
        <iframe src="http://arapehlivanian.com"></iframe>
      </div>
    </div>
    

### Explanation

The solution is fairly straightforward. Because the bug is caused by the float, we remove the float from the div that contains the iframe. However, in order to make sure that the div still behaves as though its floating, we assign it the `display: table-cell;` rule. In order to make sure that this rule is also respected in Safari, we add the additional `display: table;` rule to the parent div&#8212;which isn&#8217;t required in Firefox. None of this is an issue in IE as it ignores both the `table` and `table-cell` values and floats the trailing div nonetheless (unless you `clear: left` it).

I hope I didn&#8217;t leave anything out. Of course, you may need to tweak this code for your own purposes but the core of it works just fine. Enjoy, and let me know if this helped you.