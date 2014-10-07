---
title: On Event Throttling
author: Ara Pehlivanian
excerpt: Throttling the onresize event in IE.
layout: post
permalink: /on-event-throttling/
tags:
  - best practices
  - event
  - event throttling
  - events
  - Feature
  - javascript
  - onresize
  - resize
  - throttle
  - throttling
  - trigger
  - web development
yourls_shorturl:
  - http://a12n.com/5c
categories:
  - General
---
### The Problem

Recently I had to use the `window` object&#8217;s `onresize` event in a project I was working on. I needed it in order to reposition some elements on a page whenever the browser&#8217;s window size changed. The trouble was, the function was *relatively* intense and was causing IE to choke. The reason? [Different browsers fire the event at different intervals][1]. In Firefox, it fires only once the user stops resizing the window. In IE, it fires continuously while the user is resizing the window. This of course, meant that IE was trying to run my function once every millisecond or so.

<!--more-->

    window.onresize = function () {
        // Do something, just nothing intense for IE's sake
    }

### The Solution

The solution is event throttling, something that [Christian Heilmann][2] had mentioned to me once before. Here&#8217;s how my flavour of it works:

    var timeoutId;
    
    /**
     * Throttles a resize event.
     * @param {Function} fn  The function to execute
     */
    function throttleResize(fn) {
        window.onresize = function () {
            window.clearTimeout(timeoutId);
            timeoutId = window.setTimeout(
                function () {
                    fn.call();
                },
                250);
        };
    }
    
    /**
     * Just a function to fire on resize
     */
    function doSomething() {
        alert("I've been resized!");
    }
    
    /**
     * Set up the throttle
     */
    throttleResize(doSomething);

As you can see, I&#8217;m setting the `onresize` event for the `window` object as you normally would. The difference is, I&#8217;m only [calling][3] my `doSomething` function after a 250 millisecond delay. The way I do this is to simply use the `window` object&#8217;s `setTimeout` method, with a catch. The trick is to clear the `setTimeout` method I&#8217;d previously set before setting it again. This effectively resets the timer every time the `onresize` event fires until it&#8217;s done firing.

### Getting Fancy

The continuous triggering of the `onresize` seems to be limited to IE, though I think I saw it in Safari 3 Beta for Windows as well. At any rate, this can be managed with an `if`/`else` block that checks to see which browser is running the code and either wrapping the function with the timer or not. I&#8217;ve found [YUI][4]&#8216;s `<a href="http://developer.yahoo.com/yui/docs/YAHOO.env.ua.html">YAHOO.env.ua</a>` works quite well at identifying the browser. But for simplicity&#8217;s sake, I&#8217;ll manually verify if we&#8217;re in Firefox or not for this example. Here&#8217;s the same code with the differentiation applied:

    var timeoutId;
    
    /**
     * Throttles a resize event.
     * @param {Function} fn  The function to execute
     */
    function throttleResize(fn) {
        if (navigator.userAgent.indexOf("Gecko") === -1) {
            window.onresize = function () {
                window.clearTimeout(window.timeoutId);
                window.timeoutId = window.setTimeout(
                    function () {
                        fn.call();
                    },
                    250);
            };
        } else {
            window.onresize = function () {
                fn.call();
            };
        }
    }
    
    /**
     * Just a function to fire on resize
     */
    function doSomething() {
        alert("I've been resized!");
    }
    
    /**
     * Set up the throttle
     */
    throttleResize(doSomething);

**It&#8217;s important to note** that if your `onresize` event handler modifies the height of the `body` element, you&#8217;ll be inadvertently re-triggering the `onresize` event in IE. You can read more about this phenomenon and how to deal with it in Jonathan Snook&#8217;s post, *[IE Fires Onresize When Body Resizes][5]*.

 [1]: http://www.quirksmode.org/js/events_compinfo.html#t03
 [2]: http://wait-till-i.com
 [3]: http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference:Objects:Function:call
 [4]: http://developer.yahoo.com/yui/
 [5]: http://snook.ca/archives/javascript/ie6_fires_onresize/