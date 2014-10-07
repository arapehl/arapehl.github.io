---
title: The C in CSS Stands for Cascade
author: Ara Pehlivanian
layout: post
permalink: /the-c-in-css-stands-for-cascade/
tags:
  - cascade
  - css
  - html
  - style
  - web
  - web dev
  - web development
yourls_shorturl:
  - http://a12n.com/5y
categories:
  - General
---
People have a propensity to see a one-to-one relationship between an element and its look. In other words, they see an element as being styled much like if you were to paint something with a paint brush, a one-off job. At least that&#8217;s the way things were circa the early 1990&#8217;s with `font` tags and inline styling attributes such as `bgcolor`. This meant a *lot* of work to style a page, and once it was done, it was on to the *next* page and a whole lot *more* work. Of course work isn&#8217;t a bad thing, and nobody can fault you for working hard. But working needlessly? That&#8217;s another story.

In 1994 Håkon Wium Lie and Bert Bos [collaborated on Cascading Style Sheets][1]. The idea was that styles could inherit or cascade from one another. This marked a fundamental shift in the way an HTML document could be styled. It was now possible to affect the look of all of the elements of a certain type in a page and throughout a site with just one rule.

    p {
        color: red;
    }

This rule for example would colour the text in all paragraph elements red. If, however, you wanted one particular paragraph&#8217;s text to be coloured blue, you could assign it an ID and target it specifically.

    p#intro {
        color: blue;
    }

Here the text of the paragraph element with the ID `intro` will be coloured blue. Note however that all paragraphs are coloured red and only one is blue. The latter is originally red as well but is then overridden by a more specific rule and becomes blue. Hence the cascade. Taking advantage of this sort of broad stroke styling allows for very easy maintenance and updating of a site.

It&#8217;s therefore tragic when an old school one-to-one mentality is applied using CSS. Take for example this bit of code:

    p#welcome {
        color: black;
        font-size: 115%;
    }
    
    p#about {
        color: black;
        font-size: 115%;
    }
    
    p#sale {
        color: red;
        font-size: 115%;
    }
    
    p#contact {
        color: black;
        font-size: 115%;
    }

Here we have four style rules that do pretty much the same thing. The only difference is that the paragraph with the ID `sale` is coloured red. This CSS would be much more efficient if it took advantage of the cascade.

    p {
        color: black;
        font-size: 115%;
    }
    
    p#sale {
        color: red;
    }

Note how the `sale` paragraph doesn&#8217;t have a `font-size` rule. That&#8217;s because it inherits its font size from the basic rule that applies to all paragraphs. This makes maintenance much easier.

So remember: leverage the cascade, it will make life a lot easier for you when maintaining (and even debugging) a site.

 [1]: http://en.wikipedia.org/wiki/Cascading_Style_Sheets#History