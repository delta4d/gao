---
layout: post
title: "get ri work"
date: 2016-02-20 12:58:35
categories: ["ruby"]
tags: []
---

After a fresh install of ruby, `ri sth.` may get nothing, to get it work, we
can install rdoc-data.

```
gem install rdoc-data
rdoc-data --install
```

To generate doc for gems

```
gem rdoc --all --overwrite
```
