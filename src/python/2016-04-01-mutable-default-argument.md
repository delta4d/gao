---
layout: post
title: "mutable default argument"
date: 2016-04-01 21:06:56
categories: ["python"]
tags: []
---

OK, look at the following code..

```python
def quux(x, l=[]):
    l.append(x)
    print(l)

quux(1) # [1]
quux(2) # [1, 2]
quux(3) # [1, 2, 3]
```

In python, the default argument is evaluated only once.
Suppose `[]` has a handle `p`, first we have `p=[]`, then
after `quux(1)`, `p=[1]`, then we call `quux(2)`, the argument
`l` is evaluated to `p` again, that is `[1]`, results `[1, 2]` after.

The problem is that `list` is mutable in python, and as a
result, don't use mutable default argument in python.

At first looking at [python tutorial][1], I did not understand it, now as thinking of _handle_, I finally understand it. It is basically the same as then
following code.

```python
x = []
y = x
y.append(1)
print(x) # => [1]
```

In python, the atom type like `int` is immutable, `str`, `tuple` is also immutable.

---

1. https://docs.python.org/3/tutorial/controlflow.html#default-argument-values

[1]: https://docs.python.org/3/tutorial/controlflow.html#default-argument-values
