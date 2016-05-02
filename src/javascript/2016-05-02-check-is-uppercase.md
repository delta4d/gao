---
layout: post
title: "check is uppercase"
date: 2016-05-02 17:37:06
categories: ["javascript"]
tags: []
---

Javascript does not have `isupper` by default, you have to write your own function.

The most obvious method is `'A' <= x && x <= 'Z'`, and on [stackoverflow][soup],
it uses `x == x.toUpperCase()`, which will return true if `x` is not lowercase
letter.

[soup]: http://stackoverflow.com/questions/1027224/how-can-i-test-if-a-letter-in-a-string-is-uppercase-or-lowercase-using-javascrip

I am really new to javascript, and still can not figure out why it should be like
that.

In javascript, there is no `char`, `'X'` is just a singleton string, and what surprise
me is that `<=` on numbers is still compared as strings. So, maybe the following
method is ok?

```javascript
String.prototype.isUpperCase = function() {
    if (this.length !== 1) return false;
    return 'A' <= this && this <= 'Z';
}
```
