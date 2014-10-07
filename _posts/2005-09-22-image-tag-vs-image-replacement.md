---
title: Image tag vs. Image replacement
author: Ara Pehlivanian
layout: post
permalink: /image-tag-vs-image-replacement/
tags:
  - css
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/5e
categories:
  - General
---
One of the most regularly recurring questions that I have to answer when building a site is: &#8220;should I use an [image tag][1] here, or a CSS image replacement?&#8221; This is especially the case when working with a design that&#8217;s been given to me by a graphic designer, because I&#8217;m not the one who thought out the design. When I work on a design from the beginning, I approach it with the mindset of a web developer. I consider what elements will be lists, what will be headings, etc. Even while working on a purely graphical design. That&#8217;s both good and bad. Good because I can foresee and circumvent potential implementation pitfalls. Bad because of its limiting factor on creativity.

In the past, &#8220;image tag or not&#8221; wasn&#8217;t even an issue. You wanted an image, you used an image tag. But now, with [Web Standards][2] and a focus on semantics, I have to carefully consider the meaning of every element that goes into the page. So, in order too answer one question, I need to ask another: &#8220;what does this image represent?&#8221; Is it a product? A brand? A design element like a rounded corner? Or a particularly nice font that you can&#8217;t get without using an image?

> When trying to decide whether to use an image tag or not, ask yourself: &#8220;what does this image represent?&#8221;

Depending on your answer, you&#8217;ve got three possible options:

For design elements use background images
:   If your image represents a design element such as a [rounded corner][3], it has no semantic value and should have no impact on the actual content of the page. For implementations such as these, [background images][4] are the best.

For products, brands and other tangible elements, use the image tag
:   If your image represents a product, then it&#8217;s a quantitative part of your content and should therefore be represented semantically with an image tag. Take for example [these][5] [sites][6]. If you view the pages without stylesheets you&#8217;ll see that only the products themselves use the image tag. Everything else is rendered using the `background-image` CSS property. Likewise, [*this* site][7]&#8216;s brand is preserved by the use of an image tag.

When styling content, use an image replacement technique
:   In the case where you&#8217;ve got actual content that needs styling, such as a headline that needs to be in a specific typeface, then use one of the [many available image replacement techniques][8].

All of this really amounts to using the right tool for the right job. And in the end, isn&#8217;t that what web standards are all about?

 [1]: http://www.htmlhelp.com/reference/html40/special/img.html
 [2]: http://www.webstandards.org/
 [3]: http://www.alistapart.com/articles/mountaintop/
 [4]: http://www.w3schools.com/css/pr_background-image.asp
 [5]: http://www.leejeans.com/product-thumbnails.asp?group=mens&label=authentics
 [6]: http://www.chevrolet.com/cars/
 [7]: http://www.att.com/
 [8]: http://www.google.com/search?hl=en&lr=&safe=active&q=CSS+image+replacement