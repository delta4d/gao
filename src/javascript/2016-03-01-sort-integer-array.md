---
layout: post
title: "sort integer array"
date: 2016-03-01 14:11:41
categories: ["javascript"]
tags: []
---

An unexpected problem. It is different from other languages, the default behavior
is like string comparison.

```javascript
var x = [1, 11, 2].sort();
console.log(x); // [ 1, 11, 2 ]
```

We need to pass the comparison function explicitly.

```javascript
var x = [1, 11, 2].sort((a, b) => a - b);
console.log(x); // [ 1, 2, 11 ]
```

`a-b` is not the best solution because of integer overflow. Instead,
we can use `(a, b) => return a < b ? -1 : ( a == b ? 0 : 1 )`;

---

1. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
