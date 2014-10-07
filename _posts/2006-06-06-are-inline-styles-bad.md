---
title: Are inline styles bad?
author: Ara Pehlivanian
excerpt: "There's been a little talk lately on the topic of whether or not it's right to use inline styles. Here's what I think."
layout: post
permalink: /are-inline-styles-bad/
tags:
  - css
  - standards
  - web development
  - xhtml
yourls_shorturl:
  - http://a12n.com/4e
categories:
  - General
---
<p class="aside">
  Posted originally as a comment on <a href="http://www.456bereastreet.com/archive/200606/why_is_the_style_attribute_allowed_in_strict_doctypes/#comment8">456 Berea Street</a>. I had also originally posted a comment on this very same topic on <a href="http://friendlybit.com/html/inline-css-should-not-be-allowed-in-strict-doctypes/">Emil Stenström&#8217;s Friendly Bit</a>.
</p>

<p class="embellished0">
  <img id="image202" src="http://arapehlivanian.com/wp-content/uploads/2006/06/wrong_way.jpg" alt="A sign reading: Wrong Way" />I believe that the style attribute is allowed because the purpose of separation is nonetheless achieved via CSS. Whether its included directly in the page via inline styles or in a separate stylesheet, the presentation and structural layers are still kept separate. You have to remember that the push behind separation came from a) the misuse of structural elements such as the paragraph tag for adding spacing and b) the use of sanctioned structural markup for presentational purposes (such as <center> and <font>). With CSS, all that is presentational is taken out of the markup and either relegated to a separate file, or to attributes within the markup which are exactly that, attributes, not actual markup. Therefore separation is maintained.
</p>

The question is then not one of separation but one of efficiency. Is it more efficient and therefore simpler to maintain when we use separate stylesheets? The answer in most cases is yes. However, if you take that approach to the extreme you begin to introduce other problems such as the difficulty of maintaining separate stylesheets for different locales in the case if image replacements etc&#8230; Or, you start *generating* stylesheets (which introduces all kinds of overhead) simply to avoid using an inline style attribute.

I think whats called for isn&#8217;t so much a fundamentalist and/or extremist approach where everything is black or white. Rather, if we are to treat our trade as the art form that it is, and if we are to call ourselves seasoned professionals, then we should implement the years of wisdom we&#8217;ve acquired and make educated judgment calls as to when and where to use the tool provided to us in the form of the style attribute.