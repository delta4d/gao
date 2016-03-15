---
layout: post
title: "endless loop"
date: 2016-03-15 20:51:26
categories: ["bash"]
tags: []
---

In C/C++, we have `for(;;)` or `while (true)`, in ruby we have `loop`,
in bash, we can use `:`.

```bash
while :
do
    # whatever
done
```

`:` is also similar to `pass` in python.

```bash
if PREDICATE; then
    : # no op
else
    # whatever
fi
```

`:` is also like `_` in python or ruby, like a placeholder.

```
$ var=ab
$ ${var/a/x}
command not found
$ : ${var/a/x}  # then everything works fine
```

`:` is also a valid identifier, look at the famous [fork bomb][] `:(){:|:&};:`.

[fork bomb]: https://en.wikipedia.org/wiki/Fork_bomb
