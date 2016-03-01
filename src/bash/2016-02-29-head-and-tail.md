---
layout: post
title: "head and tail"
date: 2016-02-29 16:50:14
categories: ["bash"]
tags: []
---

`head` and `tail` gets the first or last lines or chars of a file.
`[head|tail] -n<LINES=10> -c<CHARS>`.

```
head -n20  # first 20 lines, default is 10
tail -c20  # last 20 chars
```

One useful switch for tail is `-f`, which follows a file descriptor.
The most common usage is `tail -f <some log>` to see what happens in the
background.
