---
title: Screen Scraping and Creating a Feed with YQL and Yahoo! Pipes
author: Ara Pehlivanian
layout: post
permalink: /screen-scraping-and-creating-a-feed-with-yql-and-yahoo-pipes/
podPressPostSpecific:
  - 'a:6:{s:15:"itunes:subtitle";s:15:"##PostExcerpt##";s:14:"itunes:summary";s:15:"##PostExcerpt##";s:15:"itunes:keywords";s:17:"##WordPressCats##";s:13:"itunes:author";s:10:"##Global##";s:15:"itunes:explicit";s:2:"No";s:12:"itunes:block";s:2:"No";}'
yourls_shorturl:
  - http://a12n.com/w
categories:
  - Technology
tags:
  - explanations
  - pipes
  - rss
  - scraping
  - screen scraping
  - web development
  - yahoo
  - yahoo pipes
  - yql
---
[Dav Glass][1] recently [asked][2] if anyone could build him an RSS feed of the [YUI download][3] page using [YQL][4] and [Pipes][5]. I was somewhat confident of my Pipes and YQL skills so I decided to take a crack at it. The first thing I did was to scrape the page&#8217;s contents using YQL.

## Scraping with YQL

The [YQL Console][6] allows access to several Data Tables, among which is a whole set of tables under the category &#8220;data&#8221; that aren&#8217;t tables at all. They&#8217;re more like APIs allowing you to connect to some pretty powerful fetchers and parsers. I selected the one named &#8220;html&#8221; which allows you to access any html document on the web as a data source and parse it using xpath.

Here&#8217;s the query I fed it:

    select * from html where url="http://yuilibrary.com/downloads/?show=yui2" and xpath='//table[thead/tr/th/h2/@id="yui2"]/tbody//tr[@class="even" or @class="odd"]'

which returns the following fragment:

    <tr class="even">
        <td><a title="Version 2.7.0b" href="yui2/yui_2.7.0b.zip">Version 2.7.0b</a></td>
        <td>02/19/2009</td>
        <td><em class="md5">90778a161ce9108a23a590e5198b8116</em></td>
    </tr>
    <tr class="odd">
        <td><a title="Version 2.6.0" href="yui2/yui_2.6.0.zip">Version 2.6.0</a></td>
        <td>10/01/2008</td>
        <td><em class="md5">41bed4b882c9148cebff5dd1a0dd8727</em></td>
    </tr>
    <tr class="even">
        <td><a title="Version 2.5.2" href="yui2/yui_2.5.2.zip">Version 2.5.2</a></td>
        <td>05/28/2008</td>
        <td><em class="md5">eaadfcbcb651c50092bb679266aa3c20</em></td>
    </tr>

## Creating a Feed with Pipes

You may have noticed that I already had a problem. The link text for each of the items was not descriptive enough. If I used them as-is, people subscribing to the feed would see stuff like: &#8220;1.0.0b1&#8243; and &#8220;3.0.0 Beta 1&#8243;, which would just be confusing. Instead I wanted them to look like this: &#8220;YUI Builder &#8211; 1.0.0b1&#8243; and &#8220;YUI 3 &#8211; 3.0.0 Beta 1&#8243;. That&#8217;s why my query only targets one table at a time by its `id`. That way I can isolate each table and prefix each link text with the correct product&#8217;s name.

[Here][7]&#8216;s what doing that looked like:

[<img class="alignnone size-medium wp-image-793" title="pipes" src="http://arapehlivanian.com/wp-content/uploads/2009/06/pipes-300x158.png" alt="pipes" width="300" height="158" />][8]

You&#8217;ll note that the first thing I did after fetching the rows was to prepend the link text. Here&#8217;s where things got tricky. On my first attempt to do this, back when Dav first asked for it, I got stuck here. I wasn&#8217;t able to target the first `td` in the three that are contained in each row. Thanks to [Nagesh Susarla][9] of the YQL/Pipes team however, I was able to target the `td` I wanted by including its index number in the field targeting string like so: `item.td.0.a.content`. By including the `` in there, I&#8217;m telling YQL that I want the first `td` in the set.

After prepending the link text with the product name, I use a union operator to put the contents of all the queries together, since now I don&#8217;t need them apart anymore. Then it&#8217;s on to putting the `yuilibrary.com` domain name in front of the `href` attribute values since they weren&#8217;t there. Then I clean everything up by looping over my rows and creating clean items out of them using an Item Builder. (I could have just renamed or copied the fields I wanted and stayed with the rows as-is, but then I&#8217;d be delivering a lot of unnecessary junk in my feed.) Finally, I run the whole thing through a sort operator on the `pubDate` field (not in the screen capture) and output the result in a [feed][10].

In the end, a YQL/Pipes team member gave Dav what he needed a lot faster than I could, but hey I learned something in the process. This technique comes in pretty handy when a page doesn&#8217;t have a feed and you want to track changes on it. So now that you know how to do it, go out there and rip the web apart!

<ins datetime="2009-06-25T09:52:28+00:00"></ins>**Update**: I&#8217;m proud to say that the feed that I created has been copied and made the [feed for the YUI Downloads page][11].

 [1]: http://blog.davglass.com/
 [2]: http://twitter.com/davglass/status/1994517475
 [3]: http://yuilibrary.com/downloads/
 [4]: http://developer.yahoo.com/yql/
 [5]: http://pipes.yahoo.com/pipes/
 [6]: http://developer.yahoo.com/yql/console/
 [7]: http://pipes.yahoo.com/pipes/pipe.edit?_id=05ed54b00bf80cc43160ee19d6b18e02
 [8]: http://arapehlivanian.com/wp-content/uploads/2009/06/pipes.png
 [9]: http://nagiworld.net/
 [10]: http://pipes.yahoo.com/pipes/pipe.run?_id=05ed54b00bf80cc43160ee19d6b18e02&_render=rss
 [11]: http://feeds.feedburner.com/YuiDownloads