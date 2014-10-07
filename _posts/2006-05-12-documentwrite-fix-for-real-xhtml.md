---
title: 'document.write() fix for (real) XHTML [v0.5.1]'
author: Ara Pehlivanian
excerpt: A script that gets AdSense, the Technorati Badge and other 3rd party JavaScript working with application/xhtml+xml.
layout: post
permalink: /documentwrite-fix-for-real-xhtml/
tags:
  - dom
  - hacks
  - javascript
  - projects
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/7
categories:
  - General
---
**Please note that this page is being regularly updated as the script matures. Please check out the [changelog][1] to see what&#8217;s been added since it&#8217;s first release.**

This is a solution to a niche problem. But even niche problems need solutions. A while back I started [serving my pages with the application/xhtml+xml MIME type][2] (in other words, as XML not HTML). The trouble was that all of the third party scripts on my site that used `document.write()` to output their content stopped working. (To learn more about this issue read: [Does document.write work in XHTML?][3] and [ Why document.write() doesn&#8217;t work in XML][4].)

The solution isn&#8217;t as pretty as I had originally hoped, but it works.

My [first attempt][5] only worked with one script tag. My [second attempt][6] also worked with only one script tag, just using a different technique.

I then toyed around with an early version of the script below and it was a lot more elegant than it is now. It was more elegant because every time a document.write was called it checked to see how far along the DOM was in being built by counting the number of script tags in the page. It then dumped its contents at the last known script tag&#8217;s position. Very clean. I wish I could have used that. It&#8217;s just that it only worked in text/html mode. As soon as I switched MIME types to application/xhtml+xml, the parser stopped cooperating and everything ended up bunched together at one location (the first script tag&#8217;s position). That&#8217;s because when using the text/html MIME type you&#8217;re in the standard DOM where script tags are parsed as the DOM is being built. Not so with application/xhtml+xml. The DOM is built first and then all scripts are run afterwards. The code that&#8217;s being executed has no idea where it&#8217;s being called from in the DOM (because in real XHTML you&#8217;re [not supposed to run scripts that adjust the DOM directly in the body of the document][3]) so there&#8217;s no reference for me to point to and say &#8220;build your nodeset here&#8221;. So seeing as how there was a huge disconnect between the scripts themselves and where they were supposed to dump their contents, I had no choice but to take the route that I took.

The code supports multiple script tags as well as script tags with multiple document.write()s, something I couldn&#8217;t have hoped to support in the first two tries. The code below basically does the following:

1.  Wires up document.write so that it dumps it&#8217;s output into a stack instead of the DOM.
2.  Builds node fragments out of the contents of the stack&#8211;it relies on manually entered signatures (ugly, I know) to know when to start building a new fragment. This is done in order to support scripts containing multiple document.write()s (see the [code][7] for the [buzzboost][8] section on my feeds page for an example of such a script).
3.  Cleans up the fragments because they contain HTML errors that will cause the XML DOM parser to bomb.
4.  Extracts, creates and re-inserts a <script> node out of any fragment containing one. This is the only way to ensure that it will be run once it&#8217;s inserted into the DOM. innerHTML doesn&#8217;t do it.
5.  Finds the script tags in the page via their IDs (which are also manually entered, yuk)
6.  Inserts the fragment next to the script tag

I suppose I could cut out the need for step four by identifying the script tags by the contents of their `src` attributes, but for now I&#8217;m just happy to get this thing working. Maybe in the next version. ;-)

So far I&#8217;ve tested it on Firefox 1.5(PC), IE 6(PC), Opera 8.5(PC), IE 5.2(Mac) and Safari 1.3.1(Mac) and they all seem to work fine. Take her for a spin and let me know how it works for you!

### <head>

    <script src="DocumentWriteOverride.js"></script>
    <script>
    	window.onload = DocumentWriteOverride.Show; // of course you can bind it however you wish as long as it's on load
    </script>

### DocumentWriteOverride.js

    /*
    Document Write Override v0.5
    Written by Ara Pehlivanian (http://arapehlivanian.com)
    
    This work is licensed under a Creative Commons Licence
    
    http://creativecommons.org/licenses/by-nd/2.5/
    
    */
    
    var DocumentWriteOverride = {
    	Signatures : [
    		["dw_technorati","<p id=\"te_l\"", ""],
    		["dw_feedburner","<div class=\"feedburner", ""],
    		["dw_measuremap","<script type='text/javascript' src='http://tracker.measuremap.com", ""]
    	],
    	
    	Stack : [],
    	
    	Store : function(str){
    		DocumentWriteOverride.Stack[DocumentWriteOverride.Stack.length] = str;
    	},
    	
    	Show : function(){
    		var signatures = DocumentWriteOverride.Signatures;
    		var stack = DocumentWriteOverride.Stack;
    		var scripts = document.documentElement.getElementsByTagName("body")[0].getElementsByTagName("script");
    		var pointer = -1;
    		for(var i=0; i<stack.length; i++){
    			for(var j=0; j<signatures.length; j++){
    				if(stack[i].toString().indexOf(signatures[j][1]) != -1) pointer=j;
    			}
    			signatures[pointer][2] += stack[i];
    		}		
    		
    		for(var i=0; i<signatures.length; i++){
    			var node = document.getElementById(signatures[i][0]);
    			if(typeof node != "undefined"){
    				var str = DocumentWriteOverride.Cleaner.Clean(signatures[i][2].toString());
    				if(str.indexOf("<script") != -1){
    					var parentNodeRef = node.parentNode; //referencing the parent node directly causes the script to bomb
    					parentNodeRef.innerHTML += str.substring(0, str.indexOf("<script"));
    					DocumentWriteOverride.AddScript(parentNodeRef, str.substring(str.indexOf("<script"), str.indexOf("</script")+9));
    					parentNodeRef.innerHTML += str.substring(str.indexOf("</script")+9, str.length);
    				}else if(str.length > 0){
    					node.parentNode.innerHTML += str;
    				}
    			}
    		}
    	},
    	
    	AddScript : function(parentNodeRef, fragment){
    		var delimiter = fragment.substr(fragment.indexOf("src=") + 4, 1);
    		var start = fragment.indexOf("src=") + 5;
    		var character = fragment.substr(start, 0);
    		var src = "";
    		while(character != delimiter){
    			src += character;
    			character = fragment.substr(start++, 1);
    		}
    		var script = document.createElement("script");
    		script.type = "text/javascript";
    		script.src = src;
    		parentNodeRef.appendChild(script);
    	},
    	
    	Cleaner : {
    		Clean : function(str){
    			var tmpStr = str;
    			
    			tmpStr = this.ReplaceAll(tmpStr, "&#187 ", "&amp;#187; ");			// Technorati fix
    			tmpStr = this.ReplaceAll(tmpStr, "&#8230<", "&amp;#8230;<");		// FeedBurner fix
    			tmpStr = this.ReplaceAll(tmpStr, "&repeat=", "&amp;repeat=");	// MeasureMap fix
    			tmpStr = this.ReplaceAll(tmpStr, "&x=", "&amp;x=");				// MeasureMap fix
    			return tmpStr
    		},
    		
    		ReplaceAll : function(str, from, to){								// Hat tip to Mark for this algo (http://www.experts-exchange.com/M_1235249.html)
    			var idx = str.indexOf(from);
    			while(idx > -1){
    				str = str.replace(from, to);
    				idx = str.indexOf(from);
    			}
    			return str
    		}
    	}	
    }
    document.write = DocumentWriteOverride.Store;

### Changelog {#changelog}

*   v0.5.1 AdSense support has been removed. Google prefers that I not distribute a script that touches their code&#8211;though I was granted limited permission to use the script on my own site. Rather, they&#8217;d like to take a closer look and see if they could make AdSense XHTML compatible. Neat!
*   v0.5&#8211;Fixed Mac IE compatibility problem (and cleaned up a few typos :-/)
*   v0.4&#8211;Firmed up script-within-script support so that the script tag being written doesn&#8217;t need to occupy a whole document.write() line on it&#8217;s own.
*   v0.3&#8211;Added Measure Map support (scripts being called within scripts)
*   
*   <del>v0.2&#8211;Added AdSense support</del>
*   v0.1&#8211;Initial release

 [1]: #changelog
 [2]: http://arapehlivanian.com/2005/11/25/ive-converted-to-applicationxhtmlxml/
 [3]: http://www.w3.org/MarkUp/2004/xhtml-faq#docwrite
 [4]: http://ln.hixie.ch/?start=1091626816&#038;count=1
 [5]: http://arapehlivanian.com/2006/04/26/hacking-the-technorati-badge/ "Hacking the Technorati Badge or: How I Hacked Document.Write() in Order to Make it Work With application/xhtml+xml"
 [6]: http://arapehlivanian.com/2006/05/02/hacking-the-technorati-badge-part-deux/ "Hacking the Technorati Badge part Deux"
 [7]: http://feeds.feedburner.com/arapehlivanian?format=sigpro
 [8]: /syndication/#buzzboost