---
title: "Bookmarklet to identify those annoying x-overflows in your responsive site"
date: 2018-07-18T09:40:34+02:00
tags: [css, javascript]
draft: false
---

Is not unusual when you're adapting a desktop design to smaller devices to have some hidden element overflowing your
viewport in the x-axis and causing this annoying and undesirable horizontal scroll.

![x-overflow animation](/img/x-overflow.gif)

Sometimes it's not easy to find the element that is breaking the layout, especially if you're working on some legacy
codebase you don't really know. In those cases, I use this Javascript snippet to help me identify which element(s) are
to blame.

    document.querySelectorAll('*').forEach(function(e) {
        (e.offsetWidth > window.innerWidth ||
            e.getBoundingClientRect().right > window.innerWidth) &&
            console.log(e);
    });

Basically it iterates all the nodes in the DOM and checks which ones are wider than the viewport or which ones have
their right corner outside the viewport, logging them in the console.

You can copy-paste this snippet directly in your browser's console, but I prefer to create a bookmarklet so that I only
have to do a single click to identify the overflowing elements.

    javascript:(function(){document.querySelectorAll('*').forEach(function(e){(e.offsetWidth>window.innerWidth||e.getBoundingClientRect().right>window.innerWidth)&&console.log(e)})})();

Drag and drop this bookmarklet into your browser's bookmarks toolbar.

{{< x-overflow-bookmarklet >}}

