---
layout: post
title: "vertical center"
date: 2016-05-01 13:17:11
categories: ["css"]
tags: []
---

I am really new to css, I thought it was a simply question, but after some search
it seems not that easy.

As web page is just some flow of content, we cannot know the exactly height. So it
is hard to do exactly vertical center. But `flex` layout in css3 made it easy.

First we create a `vertical-center` container.

```html
<div class="vertical-center">
    <div class="content">
    whatever
    </div>
</div>
```

```css
.vertical-center {
    min-height: 100vh; // viewpoint height
    display: flex;     // flex layout
    aligh-items: center;
}
```

---------

1. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout
