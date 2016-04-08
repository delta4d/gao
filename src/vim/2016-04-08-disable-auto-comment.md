---
layout: post
title: "disable auto comment"
date: 2016-04-08 15:33:58
categories: ["vim"]
tags: []
---

Disable auto comment after <kbd>Enter</kbd>, <kbd>o</kbd> or <kbd>O</kbd>.
Add these lines to your vimrc file.

```vim
set formatoptions-=r " enter
set formatoptions-=o " oO
```

`:h formatoptions` for more details, `:h fo-table` for more option details.
