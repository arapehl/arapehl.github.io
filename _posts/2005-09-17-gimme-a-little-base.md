---
title: Gimme a little base
author: Ara Pehlivanian
layout: post
permalink: /gimme-a-little-base/
tags:
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/3g
categories:
  - General
---
Recently I&#8217;ve found myself in situations where I need to mess around with HTML documents for sites that I haven&#8217;t previously worked on. This means that I don&#8217;t have any of the document&#8217;s dependancies locally. Plus, some of these pages are dynamically generated, requiring that I install the appropriate environment on my machine in order to work with the file.

If you just want to play around with the HTML and you don&#8217;t want to go through all the hassle of setting up environments and copying over files here&#8217;s what you do:

1.  Copy the source of the page you want to edit into a local .html file.
2.  Insert the `<base href="" />` tag into the document `<head>` with the original domain in the `href` attribute.

That&#8217;s it. Now when you view the local HTML file, all of the images, CSS links and so on will work.