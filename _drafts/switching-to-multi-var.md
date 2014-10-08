---
title: Switching to multi-var variable declaration
author: Ara Pehlivanian
excerpt: 
layout: post
permalink: /switching-to-multi-var/
---
I recently [tweeted][1] that I was switching to multi-var variable declaration for improved readability. There are a few other reasons my decision.

## It’s debugger friendly
If you’ve ever tried stepping over a single-var declaration in a debugger you know it can be a pain.

    var fName = 'Ara',
    lName = 'Pehlivanian',
    profession = 'Pedant';

Though the declarations above are straightforward, something like this isn’t:

    var id = 42,
    fName = getFname(id),
    lName = getLName(id),
    profession = getProfession(id);

If any of those functions throws an error, you’re going to have a bad time. Since they’re all a part of one statement, stepping into one of them becomes difficult. You’d either have to step into and out of each one till you’re in the one you want or you’d have to set a breakpoint in the misbehaving one in order to stop execution at the right place.

## But it guards against hoisting issues
One argument for using a single `var` is to guard against [hoisting][2] issues since you’re forcing yourself to only use one at the top of each function. This style is debugger friendly as you can step over each assignment separately but it opens you up to other problems like accidentally making a `var` global:

    var x, y, velocity, mass;
    x = 250;
    y = 475;
    z = 322;
    velocity = 42;
    mass = 477;

In this example, I started out working in two dimensions and then added `z` but forgot to declare it. JavaScript implicitly makes `z` a global variable. You can also guard against this sort of thing by running in [strict mode][3] but either way, you’re retyping the same variable name twice.

## What about optimization?
Some people consider the extra three characters that a `var` requires to be needless weight. Though the intention is good, it’s misplaced. Size optimization should be handled in your [build][4] where a minifier can do a whole lot more for your code than just skip out on a few `var` statements.

## Readability
This brings me back to the main reason for why I switched in the first place, readability.

    var fName = 'Ara';
    var lName = 'Pehlivanian';
    var profession = 'Pedant';

A nice side-effect of using multiple `var` statements is that the variables line up and I don’t have to break indenting rules to line them all up.

As a developer, I spend a lot of time reading code. Not only is it nice to be greeted with a well-organized, neat-looking program, but it helps me understand what you’re doing a whole lot quicker if I don’t have to spend time deciphering your code. Seriously, go be clever somewhere else. Make your code as verbose as possible, you’ll thank your past self when delving back into an old program months after writing it.

[1]: https://twitter.com/ara_p/status/515618716105859072
[2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting
[3]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode
[4]: http://gruntjs.com/sample-gruntfile
[5]: http://www.amazon.com/gp/product/098733218X/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=098733218X&linkCode=as2&tag=ara_p-20&linkId=IHZCSGGUOF7UETNH
