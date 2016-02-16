---
layout: post
title: "convert any base to 10"
date: 2016-02-16 16:05:21
categories: ["bash"]
tags: []
---

In bash, there is a convient way to convert any base to 10 in the format `base#number`.

```
$ echo $((16#ff))
255
```

The maximum base is up to 64, include `0-9`, `a-z`, `A-Z`, `@` and `_`. It seems
there is not an universal to way to do the other way around, but we can use
`printf` to get octal or hex output.
