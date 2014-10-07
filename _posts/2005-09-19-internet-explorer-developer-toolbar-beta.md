---
title: Internet Explorer Developer Toolbar Beta
author: Ara Pehlivanian
layout: post
permalink: /internet-explorer-developer-toolbar-beta/
tags:
  - css
  - dom
  - reviews
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/6f
categories:
  - General
---
Hot on the heels (!) of [Chris Pederick’s Web Developer Firefox extension][1], Microsoft has put together the [Internet Explorer Developer Toolbar Beta][2].

The first thing you’ll notice when you install it is how plain it looks. No logo, no icons, just plain text buttons, which makes it hard to use since you don’t know if a button is hiding a dropdown or if it’s going to pop up a window. I’m writing this one off to it still being in Beta.

One of the most useful tools that I can no longer work without is Firefox’s DOM Inspector. Now, finally, IE has its own “View DOM” button in the toolbar. It allows you to traverse the DOM, but doesn’t have that handy pointer you can use to localize an element by clicking directly on the page. It also allows you to see and modify the CSS style rules of the element you click on, but that’s it. You can’t pinpoint which classes, in what sequence, from which sources apply to the element (like you can in the DOM Inspector).

One feature that it has which its Firefox counterpart doesn&#8217;t is the ability to highlight elements by positioning type. So if you want to see for example, all of the elements that are positioned relatively, or absolutely, you can.

For the most part though, a lot of the functionality you get with the Web Developer Firefox extension is replicated in the IE Developer Toolbar. But it’s obvious that it’s a first step, as a lot of the features are relatively limited and/or basic. But basic or not, it’s a toolbox that any serious web developer will welcome with open arms.

In an ironic footnote: I used the IE Developer Toolbar to validate the download page where I got it from and it returned [35 HTML errors][3] and a [lot of CSS errors][4].

 [1]: http://chrispederick.com/work/firefox/webdeveloper/download/
 [2]: http://www.microsoft.com/downloads/details.aspx?FamilyID=e59c3964-672d-4511-bb3e-2d5e1db91038&displaylang=en
 [3]: http://validator.w3.org/check?verbose=1&uri=http://www.microsoft.com/downloads/details.aspx?FamilyID=e59c3964-672d-4511-bb3e-2d5e1db91038&displaylang=en
 [4]: http://jigsaw.w3.org/css-validator/validator?profile=css2&warning=2&uri=http://www.microsoft.com/downloads/details.aspx?FamilyID=e59c3964-672d-4511-bb3e-2d5e1db91038&displaylang=en