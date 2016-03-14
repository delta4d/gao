---
layout: post
title: "parameter expansion"
date: 2016-03-14 23:48:16
categories: ["bash"]
tags: []
---

I know this a very long time, but I never really use it, and never thought about
it seriously, I thought it was hard to remember.

```
$ var=x.x.Y.Y
$ echo ${var:2}      # slice
x.Y.Y
$ echo ${var:2:-1}
x.Y
$ echo ${var/./ }    # substitute
x x.Y.Y
$ echo ${var//./ }
x x Y Y
$ echo ${var#*.}     # cut prefix
x.Y.Y
$ echo ${var##*.}
Y
$ echo ${var%.*}     # cut suffix
x.x.Y
$ echo ${var%%.*}
x
$ echo ${var^x}      # toupper
X.x.Y.Y
$ echo ${var^^x}
X.X.Y.Y
$ echo ${var,Y}      # tolower
x.x.y.Y
$ echo ${var,,Y}
x.x.y.y
```

At first, it seems a little messy, but after some observation, it is easy to
understand, not only to remember.

`st:ed/length` is similar to python's _slice_, but the negative number
have different meaning, here `-1` stands for last 2, not last 1, if you want
a suffix, just don't supply the second parameter is OK. When the second
parameter is non-negative, it stands for the length, not the ending position.
By the way, python's slice got a beautiful symmetry, `s[i:] + s[:i] == s`.

`/pattern/text` is similar to vim's replace, in order to do global search,
use `//pattern/text`, not `/what/ever/g`, and all the other parameter expansion
are all the same, if you want a global operation.

`#` is used to cut prefix, `%` is used to cut suffix. What? Why choose these
two weird symbols? Ha! Look at what is around `$` in your keyboard, it should
explain. `##` and `%%` is greedy, of course. `#prefix_pattern` or `%suffix_pattern`.

`^` and `,` is about upper or lower case, and as we see, hat is of course to
uppercase letter, comma is used for lowercase. `^^` and `,,` is greedy.
`^pattern` or `,pattern`.

Recently, I begin to realize many tools is about `pattern/action`.
Such as grep, sed, awk, lex, we just first make a pattern, like regex, or text
range, get what we want, and then do some action, like print, delete, replace.

As for shell parameter expansion, the _action_ part is replaced with some
cryptic symbols, but the pattern part is still the same, and be aware that
you can use wildcards supported by the shell in pattern.

```
$ var=a.b.c.d
$ echo ${var//[ac]/}
.b..d
$ echo ${var^^[[:alpha:]]}
A.B.C.D
```

And a common usage of `#` and `%` is to get file basename and extension.

---

1. https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html
