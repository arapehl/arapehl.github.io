---
title: How to get out of a nasty RickRoll
author: Ara Pehlivanian
excerpt: "RickRolling is fine until it gets out of hand, here's how to get out of one of the worst ones yet."
layout: post
permalink: /how-to-get-out-of-a-nasty-rickroll/
tags:
  - help
  - how to
  - howto
  - internetisseriousbusiness
  - nasty
  - rickroll
  - virus
yourls_shorturl:
  - http://a12n.com/v
categories:
  - General
---
Yesterday I got [RickRolled][1] (again), which isn&#8217;t so bad, except that this one did everything it could to act like a virus and not just a prank.

The offending link is `http://internetisseriousbusiness.com/` (**don&#8217;t go there!**).

<div class="media">
  <img src='http://arapehlivanian.com/wp-content/uploads/2008/03/internetisseriousbusiness.jpg' alt='Screen shot of internetisseriousbusiness.com' />
</div>

It resizes your browser and starts playing Rick Astley&#8217;s &#8220;Never Gonna Give You Up,&#8221; while moving the browser window into all four corners of the screen, again not so bad. Here&#8217;s the nasty part: *you can&#8217;t close the window*.

The page has an `onbeforeunload` event handler that gets triggered when a window/tab close attempt is made. It throws up an `alert box` with part of the song&#8217;s lyrics in it. Closing it just opens up another `alert box` effectively keeping you from ever closing the window. Most people have no choice but to force quit their browser, but here&#8217;s how to get out without losing everything you&#8217;re working on:

1.  Keep your finger down on the Esc key till there are no more `alert box`es
2.  Turn off JavaScript <small>(this is easier if you have a tool like the <a href="http://chrispederick.com/work/web-developer/">Web Developer Toolbar</a> Firefox add-on or the <a href="http://www.microsoft.com/downloads/details.aspx?familyid=e59c3964-672d-4511-bb3e-2d5e1db91038&#038;displaylang=en">Internet Explorer Developer Toolbar</a>)</small>
3.  Close the offending window
4.  Throttle the jerk who RickRolled you

The [Whois][2] information for http://internetisseriousbusiness.com/ is:

<pre>Domain Name: INTERNETISSERIOUSBUSINESS.COM
Registrar: GODADDY.COM, INC.
Whois Server: whois.godaddy.com
Referral URL: http://registrar.godaddy.com
Name Server: NS43.DOMAINCONTROL.COM
Name Server: NS44.DOMAINCONTROL.COM
Status: clientRenewProhibited
Status: clientTransferProhibited
Status: clientUpdateProhibited
Status: clientDeleteProhibited
Updated Date: 28-jan-2008
Creation Date: 08-mar-2007
Expiration Date: 08-mar-2009</pre>

 [1]: http://en.wikipedia.org/wiki/Never_Gonna_Give_You_Up#.22Rickroll.22_Internet_meme
 [2]: http://reports.internic.net/cgi/whois?whois_nic=internetisseriousbusiness.com&#038;type=domain