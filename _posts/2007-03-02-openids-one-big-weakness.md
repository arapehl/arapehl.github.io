---
title: 'OpenID&#8217;s one big weakness'
author: Ara Pehlivanian
excerpt: "OpenID and Achilles' heel may have more in common than you think."
layout: post
permalink: /openids-one-big-weakness/
tags:
  - reviews
yourls_shorturl:
  - http://a12n.com/4h
---
Over the past couple of days I&#8217;ve come across a plethora of [OpenID][1] mentions, most notably in [episode 3 of the .net magazine podcast][2] in which the panelists discuss [Microsoft&#8217;s recent announcement][3] that they too will be supporting OpenID.

The increased hits my brain got with the OpenID keyword tweaked my interest and at around 1am last night I implemented the [phpMyID][4] identity provider on my personal website. The fact that I was able to do so with relative ease made me very happy. I began evangelizing at work today, telling people of the virtues and sheer awesomeness of OpenID. I even illustrated on my white board how you could log in to a number of different sites using the same central authentication service. Then it happened. I tried logging into [claimID][5] and it didn&#8217;t work. I tried again, and again I had an error. I&#8217;d previously managed to log in to [Ma.gnolia][6] so I went there and tried. It also failed. That got me wondering what was wrong, and so I visited my own site to see if something was wrong with the authentication service only to find that the whole site was down. My hosting service was experiencing some difficulty and as a result not only was my site unavailable, so was my OpenID identity provider!

Right then I realized that for all of it&#8217;s awesomeness and democratizing power, OpenID has one major problem. Its greatest asset, it being centrally managed, is also its greatest weakness. In the traditional login model authentication is handled at the site you wish to access. If the authentication is broken, chances are the site is down and the point is moot. But with OpenID, if your authentication provider (in my case my site) is down, then you can&#8217;t access anything&#8211;assuming adoption of OpenID really takes off.

It&#8217;s therefore imperative to OpenID&#8217;s success that there be contingency plans and services in place for this sort of thing. Secondary authentication services that you can resort to, or maybe the retaining of traditional logins in case your OpenID provider is offline for some reason. Otherwise, OpenID and Achilles&#8217; heel may one day be synonymous.

 [1]: http://openid.net/
 [2]: http://www.netmag.co.uk/zine/podcast/episode-3-1
 [3]: http://blog.wired.com/27bstroke6/2007/02/microsoft_to_su.html
 [4]: http://siege.org/projects/phpMyID/
 [5]: http://claimID.com
 [6]: http://ma.gnolia.com/