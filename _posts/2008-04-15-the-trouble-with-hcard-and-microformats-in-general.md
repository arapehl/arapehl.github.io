---
title: The Trouble With hCard and Microformats in General
author: Ara Pehlivanian
layout: post
permalink: /the-trouble-with-hcard-and-microformats-in-general/
yourls_shorturl:
  - http://a12n.com/1n
categories:
  - General
tags:
  - hcard
  - i18n
  - internationalization
  - microformats
  - vcard
  - web development
---
If you haven&#8217;t already heard of [Microformats][1], they <q cite="http://microformats.org/about/">are a set of simple, open data formats built upon existing and widely adopted standards.</q> Basically, they allow you to use a combination of class names to mark up data in your page along the same lines as existing data formats. So for example, you&#8217;d mark up contact info on a page using class names based on the popular [vCard format][2]. The resulting markup would be an [hCard][3]. In essence, Microformats aren&#8217;t in the business of reinventing the wheel, they&#8217;re all about reuse of existing patterns, and therein lie their genius.

    <span class="tel">
        <span class="type">home</span>:
        <span class="value">+1.415.555.1212</span>
    </span>

<p class="fc">
  An example of an hCard from: <cite>http://microformats.org/wiki/hcard</cite>
</p>

There is however, one glaring problem with Microformats and I ran into it head on when I was marking up a page in French. Since property values need to be in the clear (in this case, &#8220;home&#8221;), and those values need to follow an established format (in this case vCard), you can&#8217;t use any other language but English. Yep, you heard me, Microformats (at least hCard) are **English only**. So much for i18n.

    <span class="tel">
        <span class="type"><span class="err">Téléphone</span></span>:
        <span class="value">+1.415.555.1212</span>
    </span>

<p class="fc">
  An example of an invalid hCard due to a property value in French
</p>

I think that the defining difference between hCard and vCard is that the former *needs* to have its property values in cleartext whereas I don&#8217;t think the latter does. In other words, you can exchange vCards containing English property values using Japanese applications and since the vCard is simply a file, the Japanese app can open it up, read the properties in English and then display them with Japanese labels.

I tried [discussing the issue][4] with the Microformats community, but the results were far from conclusive. I was told that the `abbr` property could be used to remedy this situation, however the spec doesn&#8217;t discuss this in terms of i18n. Rather the intended use of `abbr` is to differentiate between human and machine readable formats of the same content. For example dates:

    <abbr title="2008-04-15T00:00:00">April 15th, 2008</abbr>

If I&#8217;m way off base here or Microformats have evolved since to include i18n, please by all means let me know in the comments.

 [1]: http://microformats.org/
 [2]: http://en.wikipedia.org/wiki/VCard
 [3]: http://microformats.org/wiki/hcard
 [4]: http://microformats.org/discuss/mail/microformats-discuss/2007-March/009088.html

 *[i18n]: internationalization