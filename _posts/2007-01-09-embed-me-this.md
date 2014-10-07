---
title: Embed me this
author: Ara Pehlivanian
excerpt: "One of the web development community's best kept secrets."
layout: post
permalink: /embed-me-this/
tags:
  - standards
  - web development
yourls_shorturl:
  - http://a12n.com/2q
categories:
  - General
---
Trying to properly embed a Windows Media Player object using the `<embed>` tag inside an `<object>` tag has got to be one of the most frustrating experiences of my web development life! Microsoft&#8217;s MSDN does a fine job of listing all of the possible parameters you can pass the `<object>` via `<param />` tags, but try and find the attributes for the `<embed>` tag! Nothing, nada, zip, zilch! Good luck! For obvious reasons Microsoft doesn&#8217;t list them (since the `object` tag is what you&#8217;re supposed to be using and the `embed` tag is used by their competitor Mozilla). And Mozilla doesn&#8217;t have an official set of parameters because Windows Media Player is a Microsoft product!

Well kick me in the head and call me happy! What the heck&#8217;s a guy supposed to do? I&#8217;ve &#8220;viewed source&#8221; on dozens of sites only to come up with twice as many variations of potential attributes. It seems there was an original `embed` tag or two written back in 1996 and ever since then web developers have been mixing and matching and inventing attributes as they go along. Half the stuff on most sites don&#8217;t even make sense, let alone do anything!

I&#8217;m begging, please. If you know of a site somewhere that has an official set of attributes to pass the `embed` object of `type="application/x-mplayer2"`, then please, please, please let me know. Oh and by the way, Microsoft themselves point you to the Netscape website for the `embed` reference and the link is **broken**!

<small>P.S.: I <strong>know</strong> that the industry standard is to stream video using Flash and I <strong>know</strong> that A List Apart has an article on how to do away with the <code>embed</code> tag altogether, but client constraints and the fact that the ALA method is sketchy at best keep me from going that route.</small>