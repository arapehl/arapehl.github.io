---
title: 'The Deflashifier: A fresh technique for handling alternate flash content'
author: Ara Pehlivanian
layout: post
permalink: /deflashifier/
tags:
  - flash
  - General
  - javascript
  - xhtml
yourls_shorturl:
  - http://a12n.com/2f
categories:
  - General
---
This little tidbit of code comes to us via the Schmu:

> you simply put [your] flash and your alternate content in comments (no escaping needed) [then] you call this generic function, provide it the result of the flash detection and the id of the divs to toggle
> 
> its minimal&#8230; and it works well
> 
> I havent tested it on many browsers yet&#8230;
> 
> <cite>the Schmu</cite>

    
    function SwitchFlashContent(FlashEnabled, FlashEnabled, FlashDisabled) {
    	var FlashContent;
    	if (flash7_installed) {
    		FlashContent = document.getElementById(FlashEnabled);
    	} else {
    		FlashContent = document.getElementById(FlashDisabled);
    	}
    	strFlashContent = FlashContent.firstChild.text+"";
    	strFlashContent = strFlashContent.replace(';<!--';,';';);
    	strFlashContent = strFlashContent.replace(';-->';,';';);
    	FlashContent.innerHTML = strFlashContent;
    }