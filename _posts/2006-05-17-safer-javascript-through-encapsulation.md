---
title: Safer JavaScript through Encapsulation
author: Ara Pehlivanian
layout: post
permalink: /safer-javascript-through-encapsulation/
tags:
  - best practices
  - javascript
  - web development
yourls_shorturl:
  - http://a12n.com/3l
categories:
  - General
---
Not everyone writes 100% of their JavaScript. With sites like [The JavaScript Source][1] and [JavaScript Kit][2] it&#8217;s easy to just copy and paste a bit of free code to quickly get some desired functionality on your site. The trouble is, because there are about as many authors as there are scripts in those libraries, you will inevitably start running into trouble with conflicting variable and function names as you incorporate more and more scripts.

Let&#8217;s say for example, that I want to run this [roman numeral conversion script][3] in the footer of my site so that the copyright year is automatically converted into roman numerals. Then for fun, I want to include this [random number game][4] on one of my pages. Unfortunately this scenario poses a problem. Both scripts use a global function called `Init()`.

The traditional way of getting around this problem was renaming the functions to something more specific. So the `Init()`s would become `InitRoman()` and `InitRand()` respectively for both scripts. But not only is that annoying to have to do&#8211;especially if it isn&#8217;t your own code&#8211;but it&#8217;s also very messy.

Luckily there is a cleaner, better way around the problem. It&#8217;s done by using object oriented programming principles. Though JavaScript isn&#8217;t a fully fledged <acronym title="Object Oriented">OO</acronym> language, it does support similar behaviour, such as encapsulation. <q cite="http://www.answers.com/topic/object-oriented-programming"><a href="http://www.answers.com/topic/object-oriented-programming">Encapsulation</a> ensures good code modularity, which keeps routines separate and less prone to conflict with each other.</q>

With that in mind, let&#8217;s take a look at how we can fix the conflicting `Init()` function problem. Rather than doing this:

    function InitRoman(){
    	//roman numeral initialization code here
    }
    
    function InitRand(){
    	//random number game initialization code here
    }
    
    InitRoman();
    InitRand();

we can do this:

    var Roman = {
    	Init : function(){
    		//roman numeral initialization code here
    	}
    }
    
    var Rand = {
    	Init : function(){
    		//random number game initialization code here
    	}
    }
    
    Roman.Init();
    Rand.Init();

Now isn&#8217;t that a lot nicer to look at and work with? With encapsulation you get to keep your `Init()` function name for both scripts without any conflicts.

The only thing is, of course, that if you&#8217;re copying and pasting scripts from all over the &#8216;net you&#8217;re kind of at the mercy of the authors of those scripts and will be waiting a long time for them to apply encapsulation to their existing code.

 [1]: http://javascript.internet.com/
 [2]: http://www.javascriptkit.com/
 [3]: http://javascript.internet.com/page-details/roman-numerals.html
 [4]: http://javascript.internet.com/games/random-number.html