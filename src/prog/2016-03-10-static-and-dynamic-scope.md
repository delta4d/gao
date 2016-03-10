---
layout: post
title: "static and dynamic scope"
date: 2016-03-10 13:55:03
categories: ["prog"]
tags: []
---

I can't say I fully understand the difference, but I finally understand what
the word means. Maybe it is because I am not a native English speaker, many
computer words are not that obvious to me.

Static means the scope are determined in lexical analysis, so it is also called
lexical scope. Dynamic, on the other side, is based on the call stack, it is
dynamic. Most modern programming language is static scope.

```javascript
// javascript
function f() {
    console.log(a)
}

function g() {
    var a = 'g()';
    f()
}

var a = 'static scope'

g() // -> static scope
```

```bash
# bash
function f {
    echo $a
}

function g {
    local a='dynamic scope'
    f
}

g # -> dynamic scope
```
