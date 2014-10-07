---
title: 'Bad application behaviour: stealing focus'
author: Ara Pehlivanian
excerpt: 'Apps should <strong>not</strong> steal focus by default.'
layout: post
permalink: /bad-application-behaviour-stealing-focus/
tags:
  - General
yourls_shorturl:
  - http://a12n.com/3s
categories:
  - General
---
If you use Google Talk you&#8217;re probably accustomed to this scenario. You&#8217;re typing along in a window doing some work when all of a sudden a Google Talk window pops up in your face, steals the focus and half of what you were typing ends up in the Google Talk input field.

Apps stealing focus while I&#8217;m working is one of my pet peeves. It just happened to me again while I was working in [Eclipse][1]. I had run a project wide search for a particular term and was stepping through the results using the &#8220;next&#8221; arrow button when the Console tab decided to steal focus in order to dump some information. The result? Well the &#8220;stop server&#8221; button just happens to be located exactly where the &#8220;next&#8221; button was, so my inevitable accidental click resulted in a stopped server. What a pain.

<img id="image286" src="http://arapehlivanian.com/wp-content/uploads/2007/02/stealfocus.gif" alt="Stealing focus" />

You may be thinking &#8220;yeah but you can just configure&#8230;&#8221;, no! I don&#8217;t want to have to configure every app I install for it to behave. Apps should **not** steal focus by default.

 [1]: http://www.eclipse.org/