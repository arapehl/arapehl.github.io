---
title: 'Automated Multi-Column Lists: CSS Swag Redux'
author: Ara Pehlivanian
layout: post
permalink: /automated-multi-column-lists/
tags:
  - css
  - dom
  - javascript
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/1r
categories:
  - General
---
In [A List Apart: CSS Swag: Multi-Column Lists][1], [Paul Novitski][2] walks us through the process of making ordered and unordered lists wrap vertically. A behaviour that modern browsers don&#8217;t support natively. Three of the examples (4, 5, & 6) make use of list item level class names that ultimately control the position of the columns. Wouldn&#8217;t it be nice though to avoid having to maintain class names and tweak the CSS every time you modify the content?

Well, since the third arm of web standards is the DOM, and it can be manipulated through scripting, I figured "hey, why not automate the process?" I chose to go with Paul&#8217;s [sixth][3] technique as it seemed the most elegant but tag heavy. So here it is:

<!--more-->

### As Unobtrusive as Possible

The idea was to simplify the process, so requiring you to add JavaScript calls every time you had a list would have defeated the purpose. Same thing with having to hand declare each list in an array in the document head. So I chose to identify lists who needed to be displayed in columns by their class names.

    
    <ol class="MakeColumns3">
      <li><a href="#">first</a></li>
      <li><a href="#">second</a></li>
      <li><a href="#">third</a></li>
      <li><a href="#">fourth</a></li>
    </ol>
    

The class name "MakeColumns3" identifies the list as needing to be formatted in three columns. In fact, the "MakeColumns" part of the class name is purely arbitrary and can be changed to anything you&#8217;d like. As for the number of columns, the only reason why the class name isn&#8217;t simply "3" is because it&#8217;s not valid in Mozilla/Firefox.

Once more, in the spirit of being as unobtrusive as possible, I&#8217;ve tried to pare down the amount of JavaScript that&#8217;s needed in the page to an absolute minimum. All that&#8217;s needed is one function call once the contents of the page have been loaded. There are several ways of doing this but for simplicity&#8217;s sake, I&#8217;ve put it in the body tag&#8217;s onload attribute: `<body onload="MakeColumns()">`

### Calling all lists

The first thing that the function needs to do is grab all of the ordered and unordered lists in the page:

    
    function MakeColumns()
    {
      var oLists = document.getElementsByTagName("ol");
      var uLists = document.getElementsByTagName("ul");
    

Then we call our layout function for each list whose class name begins with "MakeColumns." Since the ordered and unordered lists are stored in two separate objects the iteration and class name check have been placed in a function to avoid repeating the same code twice:

    
      CallLayoutLists(oLists);
      CallLayoutLists(uLists);
    	
      function CallLayoutLists(lists)
      {
        for(var i=0; i<lists.length; i++)
        {
          if(lists[i].className.substring(0, 11) == "MakeColumns")
          {
            LayoutList(lists[i]);
          }
        }
      }
      function LayoutList(list)
      {
    

### Laying it all out

The first thing to do is determine the number of columns. This is done by reading the remainder of the class name. The read is open ended and will grab everything after the "MakeColumns".

    
      var numColumns = parseInt(list.className.substring(11));
    

Then we grab the list items in the list and determine how many there are:

    
        var items = list.getElementsByTagName("li");
        var numItems = items.length;
        	

Now, in order to split the contents in the list as evenly as possible, we divide the items by the number of columns and keep the remainder separate. This will be needed later when we are laying the list out.

    
        var remainingItems = numItems % numColumns;
        var itemsPerColumn = (numItems - remainingItems) / numColumns;
        	

The next thing to do is to determine the column width. This could be a parameter passed to the function, but because we want to make its implementation as hassle free as possible, we determine it ourselves. What&#8217;s really nice about this method is that you can modify the width of your list items in your CSS and this code will pick it up.

So, we call GetOptimalColumnWidth() and pass it the items collection we&#8217;re currently working with. The process is pretty straightforward. All we have to do is iterate over all of the items and check their width. If their width is larger than the last entry in the variable `widest` we overwrite it. If not, we move on.

It&#8217;s very important to set the items&#8217; position to absolute because if you don&#8217;t, you won&#8217;t be able to read its proper width since by their nature, list items are block level elements and take up the entire width of their parent element. Setting their position to absolute reduces their width to that of their content.

    
        var columnWidth = GetOptimalColumnWidth(items);
    
        function GetOptimalColumnWidth(items)
        {
          var widest = 0;
          for(var i=0; i<items.length; i++)
          {
            items[i].style.position = "absolute";
            widest = (items[i].offsetWidth > widest) ? items[i].offsetWidth : widest;
          }
          return widest
        }
    

Now that we&#8217;ve gathered all of the necessary information, we begin the task of laying out the columns. We start with a loop for the number of columns we&#8217;ll be generating.

    
        for(var i = 1; i <= numColumns; i++)
        {
    

For every iteration, we reset the value of `first` to true. This is used to identify the first item in the list that will be responsible for the position of its column.

    
          var first = true;
    

Then we isolate the list items belonging to the current column and call the SetItem function to properly position the item. The beginning point for the loop is determined by multiplying the number of items per column (say 10) by the current column in base 0 (say 1), effectively skipping ahead to the appropriate column. The end point is determined by doing the same calculation but not compensating for base 0.

    
          for(var j=itemsPerColumn*(i - 1); j<itemsPerColumn*i; j++)
          {
            SetItem(items[Math.round(j)]);
          }
        }
    

The SetItem function is pretty straightforward. It&#8217;s a function because there&#8217;s another loop coming up that will use it as well.

The first thing it does with the item that it gets passed is it sets its position to relative. This is because we set it to absolute in order to determine its width earlier. Then it sets its column position by multiplying the column width by the column number it&#8217;s currently setting.

    
        function SetItem(item)
        {
          item.style.position = "relative";
          item.style.marginLeft = columnWidth * (i - 1) + "px";
    

It then makes sure to isolate the first item of the current column (set earlier in the parent loop) but not of the first column. The first column determines the base position of our list and shouldn&#8217;t be moved. All other columns need to be bumped up to where the first one is.

    
          if(first && i != 1)
          {
            item.style.marginTop = "-" + itemsPerColumn * item.offsetHeight+ "px";
            first = false;
          }
        }
    

Now earlier, we made sure that we had an even number of items per column by dividing the total number of items by the number of columns and removing (but saving) the remainder. We saved the remainder so as to tack the remaining items to the end of the last column.

Before we go into the loop, we need to reset `i` because the previous loop left it with a value larger than the number of columns. (That&#8217;s how it got out of the loop). Since we want to tack the remaining items onto the last column, we simply assign the value of `numColumns` to `i`:

    
        i = numColumns;
    

Then we loop over the remaining items and call SetItem to place them.

    
        for(var k=numItems-remainingItems; k<numItems; k++)
        {
          SetItem(items[k]);
        }
    

### IE Bug Fix

Unfortunately I haven&#8217;t been able to figure out why IE hides the first column&#8217;s bullets. Therefore one tiny little concession needs to be made by adding some padding to the left of the list:

    
    <style type="text/css">
      * html ul,
      * html ol
      {
        padding-left: 25px;
      }
    </style>
    

### Tada!

And we&#8217;re done! I&#8217;ve tested it on Mozilla/Firefox 1.0.7, IE 6 and Opera 8 (all PC) and it works on all three. Here&#8217;s an [example][4] of a page using this [script][5]. Enjoy!

 [1]: http://www.alistapart.com/articles/multicolumnlists
 [2]: http://www.alistapart.com/authors/n/paulnovitski
 [3]: http://www.alistapart.com/articles/multicolumnlists#method6
 [4]: http://arapehlivanian.com/wp-content/uploads/2005/10/columns.html
 [5]: http://arapehlivanian.com/wp-content/uploads/2005/10/columns.js