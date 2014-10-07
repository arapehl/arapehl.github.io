---
title: Worry Free JavaScript Internationalization (i18n)
author: Ara Pehlivanian
layout: post
permalink: /worry-free-javascript-internationalization-i18n/
tags:
  - best practices
  - dot notation
  - i18n
  - index notation
  - internationalization
  - javascript
  - object literal
  - web development
  - worry free
yourls_shorturl:
  - http://a12n.com/1m
categories:
  - General
---
There&#8217;s a right way and a wrong way to go about i18n. Just to be clear, I don&#8217;t subscribe to the idea of right vs. wrong unless there&#8217;s a good reason for it, otherwise I just chalk it up to preference. Sometimes I consider something as a matter of preference until someone points out a compelling argument either for or against it. It&#8217;s with that perspective that I address the issue of i18n.

I&#8217;ve often found that when first confronted with the need for i18n, the temptation is to do something like this:

    var lang = getLang();
    var msg = "";
    if (lang === "en") {
        msg = "Hello world!";
    } else if (lang === "fr") {
        msg = "Bonjour Monde !";
    }

That will work fine, but what happens if there&#8217;s a bunch of text throughout the app that needs i18n? That&#8217;s a whole lot of `if`/`else` blocks. And what happens if you suddenly have to support three, four or fifteen languages?

Object literals to the rescue! JavaScript has this wonderful little thing called the object literal represented by a set of brace brackets: `{}`. It creates a singleton object that can be nested within other objects and can contain pretty much anything. The syntax is very straight forward, all you need are key/value pairs separated by commas:

    var data = {
        helloworld: {
            en: "Hello World!",
            fr: "Bonjour Monde !"
        }
    }

In this case we have an object being assigned to a variable named `data`. That object in turn contains another object named `helloworld`. Finally, `helloworld` contains two strings, one named `en` and the other `fr`. These values can now be accessed like so:

    msg = data.helloworld.en;

Of course what we need is to be able to dynamically access the language node in our dataset. This is where index notation comes to the rescue. So far we&#8217;ve accessed our data via dot notation, but it&#8217;s also possible to access data via index notation like so:

    msg = data.helloworld["en"];

I&#8217;m sure you can see where this is going. Now that we can specify the last node of our dataset with a string value, all we need to do is substitute it with a variable.

    var lang = getLang();
    msg = data.helloworld[lang];

Here, `getLang` determines what the current language setting is and returns a string value accordingly. Once that string value has been received, it can be placed into the index portion of our data object and voila! No more `if`/`else` logic, and this technique can be used to support an infinite number of languages without ever having to modify the code itself. You want Spanish? Just add an `sp` node to your dataset. That&#8217;s it, that&#8217;s all.

Enjoy!

<ins datetime="2008-04-24T20:28:48+00:00"><strong>Update</strong>: I neglected to mention that I implemented this solution in the context of a <a href="http://widgets.yahoo.com/">Yahoo! Widget</a> where all of the data is stored locally on the desktop. This solution doesn&#8217;t make much sense in the context of a website since you&#8217;ll be sending way too much data that won&#8217;t be used down the pipe. Thanks to <a href="http://arapehlivanian.com/2008/04/13/worry-free-javascript-internationalization-i18n/#comment-40216">AB</a> for pointing out my oversight.</ins>

 *[i18n]: internationalization