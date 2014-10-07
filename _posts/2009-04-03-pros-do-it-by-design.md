---
title: Pros Do It By Design
author: Ara Pehlivanian
layout: post
permalink: /pros-do-it-by-design/
yourls_shorturl:
  - http://a12n.com/7a
categories:
  - General
tags:
  - web development
---
Whether it&#8217;s [security][1], [SEO][2], [performance][3] or [accessibility][4], retrofitting a site for any of these is always more costly than doing them *by design*.

Doing something [by design][5] means that it&#8217;s taken into consideration from the very beginning of the project and informs every decision that&#8217;s made along the way.

So for example, it would automatically be assumed that any form of user editable input would be prone to malicious attack. So all code that handles user input would first make sure to [sanitize it][6] and strip out anything but the data that it was expecting. Likewise, in the case of performance by design, all non-dynamic images would be identified in the design phase, they&#8217;d be stored on a [dedicated image server][7], given a [far future `Expires` header][8], and pushed out to [a CDN][9] for improved performance.

Of course these sorts of things *could* be done to an existing site, but they normally imply major changes in architecture which can be very expensive. Messing with a site&#8217;s architecture isn&#8217;t something that can be done haphazardly. If it isn&#8217;t done right, it could cause more problems than the ones that are being addressed. This is why I contend that experienced web developers &#8220;do it by design.&#8221; Their experience allows them to anticipate a site&#8217;s needs, and informs their decisions right from the start.

 [1]: http://developer.yahoo.com/security/
 [2]: http://www.google.com/support/webmasters/bin/answer.py?hl=en&#038;answer=35291
 [3]: http://developer.yahoo.com/performance/
 [4]: http://www.w3.org/WAI/
 [5]: http://en.wikipedia.org/wiki/Security_by_design
 [6]: http://developer.yahoo.com/security/#application
 [7]: http://developer.yahoo.com/performance/rules.html#cookie_free
 [8]: http://developer.yahoo.com/performance/rules.html#expires
 [9]: http://developer.yahoo.com/performance/rules.html#cdn

 *[SEO]: Search Engine Optimization
 *[CDN]: Content Delivery Network