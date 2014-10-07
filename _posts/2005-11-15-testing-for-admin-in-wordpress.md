---
title: Testing for Admin in WordPress
author: Ara Pehlivanian
layout: post
permalink: /testing-for-admin-in-wordpress/
tags:
  - analytics
  - moving in
  - php
  - web development
  - wordpress
yourls_shorturl:
  - http://a12n.com/40
categories:
  - General
---
Earlier today I mentioned how I came across [Google Analytics][1]. Suffice it to say, I opted to give it a try and went ahead and signed up. Once I&#8217;d gone through the process of setting up an account, I was given a snippet of code to put in my page `<head>` in order to report tracking data back to Google Analytics. The next step was to exclude myself from the stats lest I log a hit every time I visit my own site. Analytics has a feature where you can set up filters, one of which is the ability to filter by IP. Excluding my visits from work was easy enough since our Internet connection goes through a router whose IP is fixed. I ran into a problem however when I wanted to exclude myself from home. Unfortunately my ISP doesn&#8217;t give me a fixed IP so I can&#8217;t set up a filter that looks for and excludes a particular IP address. And then it dawned on me. I usually visit my own site while logged in as admin. So why not just test to see if the current visitor is logged in as Admin and if so, just don&#8217;t output the Google Analytics script tags.

Well, you&#8217;d think it would be easy enough. Not! First off I went hunting for some sort of &#8220;is\_logged\_in()&#8221; type of function. I found nothing. Then I searched high and low for something along the lines of &#8220;is_admin()&#8221; and only found a measly little post talking about a hack I could incorporate. Fine. So I followed the instructions and created a `my-hacks.php` file and put the code in it and then ran it. **BOOM!** The site crashed. Why? Because apparently the function name: `is_admin()` is already declared in `functions.php`. Okay, no problem, so I deleted my newly created `my-hacks.php` and re-ran the page. Wouldn&#8217;t you guess it, nothing happened. It&#8217;s as though `is_admin()` returned nothing. Well, I searched for documentation on the thing and came up empty handed and extremely frustrated. 

I searched, and I searched and I tried all manner of keyword combinations but found absolutely nothing on testing for admin. **Finally** I began sifting through the WordPress code and eventually came across the `$user_level` attribute which contains&#8212;duh!&#8212;the current user&#8217;s level. So I plugged that into my `if` block and &#8230; nothing. Do you know how depressingly frustrating it is to code with no prior knowledge of the language you&#8217;re working in and zero documentation to support what you&#8217;re trying to do? Anyhow, more sifting and finally I found what I needed. It seems that even though I was invoking the `get_currentuserinfo();` function which&#8212;duh!&#8212;gets the current user&#8217;s info, I hadn&#8217;t declared the `$user_level` globally and so it was never being assigned to the variable I was testing just two lines away. Hmmm&#8230; scope issue much? 

Anyhow, so now everything is honky dory and the site only logs visitor stats when visitors aren&#8217;t logged in as Admin.

You may now lambaste me with your comments about how dumb I was being and how simple this actually was and how wrong my implementation is, etc&#8230;

 [1]: http://arapehlivanian.com/2005/11/14/google-analytics/