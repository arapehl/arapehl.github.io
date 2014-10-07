---
title: A Nuance of Preventing Default
author: Ara Pehlivanian
layout: post
permalink: /a-nuance-of-preventing-default/
yourls_shorturl:
  - http://a12n.com/3y
categories:
  - General
tags:
  - anchors
  - event handler
  - events
  - javascript
  - preventDefault
  - return false
  - standards
  - web development
---
One of the most common operations when assigning event handlers is to prevent the default action the event normally triggers.

In the case of an anchor for example, the `click` event of an anchor triggers the default behaviour of following the URI specified in the `href` attribute. So the browser&#8217;s default action when clicking the &#8220;Fluffy Bunnies&#8221; anchor below, is to send the user to <http://wait-till-i.com>.

    <a href="http://wait-till-i.com">Fluffy Bunnies</a>

When coding [unobtrusive JavaScript][1] awesomeness however, following the URI isn&#8217;t always the desired action that we want when the user clicks on an anchor. Thus, the event handler that is assigned to the anchor needs to stop the default behaviour. This can be done in two ways: by having the handler `return false`, or using the event object&#8217;s `preventDefault` method (except for in IE which makes you set `returnValue` to `false` within the event object).

### Returning False

    var a = document.getElementsByTagName("a")[0];
    a.onclick = function () {
        <strong>return false;</strong>
    };

### Preventing Default

    var a = document.getElementsByTagName("a")[0];
    a.onclick = function (e) {
        e = e || event;
        if (e.preventDefault) {
            <strong>e.preventDefault();</strong> // All browsers except IE
        } else {
            <strong>e.returnValue = false;</strong> // IE
        }
    };

Having to use an `if`/`else` block every time you want to use `preventDefault`/`returnValue` is very cumbersome. This is where a good JavaScript library will serve you well by wrapping this functionality up in one easy function call. The YUI Library for example allows you to do this:

    var a = document.getElementsByTagName("a")[0];
    a.onclick = function (e) {
        e = e || event;
        <strong>YAHOO.util.Event.preventDefault(e);</strong>
    };

### The nuance: using `preventDefault` in debug vs. release code

In my opinion, `preventDefault` should be used in two different ways depending on whether you&#8217;re in debug mode or release mode. The reason for this is simple, when you&#8217;re debugging, the last thing you want is for the browser to leave your page when something breaks on clicking an anchor. Why? Because normally (in [Firebug][2] anyway) the error message that was generated disappears once you leave the page. Take the following code example:

    var a = document.getElementsByTagName("a")[0];
    a.onclick = function (e) {
        e = e || event;
        <strong>// Lots of buggy code here</strong>
        YAHOO.util.Event.preventDefault(e);
    };

In this example, the code will break before `preventDefault` has a chance to execute. Upon its breaking, the browser will fall back to the anchor&#8217;s default behaviour and leave the page to follow the anchor&#8217;s URI. That can be annoying when you&#8217;re debugging, **but** it&#8217;s **exactly** what you want in a production environment. You don&#8217;t want links to stop working in production when some JavaScript breaks. Rather, you want the script to degrade/break gracefully and give the user access to a valid URI. So the above example is fine for production. While debugging however, the following sequence is preferable:

    var a = document.getElementsByTagName("a")[0];
    a.onclick = function (e) {
        e = e || event;
        YAHOO.util.Event.preventDefault(e); // Stop the default action before buggy code breaks
        <strong>// Lots of buggy code here</strong>
    };

I hope you&#8217;ve found this nuance useful, I know it&#8217;s saved me lots of headaches when debugging.

 *[URI]: Uniform Resource Identifier
 *[IE]: Internet Explorer
 *[YUI]: Yahoo! User Interface

 [1]: http://onlinetools.org/articles/unobtrusivejavascript/
 [2]: http://www.getfirebug.com/