---
layout: post
title: "visual block edit"
date: 2016-03-03 22:34:34
categories: ["vim"]
tags: []
---

Today I finally understand why `i` not working in visual block mode.
It is because vim does not know where to insert in a block.
We can use `I` or `A` to insert at the beginning or the end of the block.
Type <kbd>c-v</kbd> or <kbd>c-q</kbd> to invoke visual block mode.

How silly I am, thought `i` may work.
Wait, maybe it could, cause the cursor is always on the border of the block.
