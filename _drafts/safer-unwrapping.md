---
title: Safer Unwrapping
author: Ara Pehlivanian
excerpt: 
layout: post
permalink: /safer-unwrapping/
---
instead of blindly unwrapping multiple layers of DOM elements using jQuery's .unwrap(), find the element itself using .closest() then grab its children() and unwrap() it. That way, you're not blindly unwrapping elements you hope to be the right one. It could happen that the element isn't there or your pointer is off and you end up unwrapping the wrong thing and breaking the page.
