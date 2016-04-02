---
layout: post
title: "python-function-arguments"
date: 2016-04-02 11:08:54
categories: ["python"]
tags: []
---

Generally, python function has the following format, `f(ps, *args, **kwargs)`.

First we have positional arguments `ps`, `*` expand list to arguments, `**` take a dict.

```python
def f(a=1, b=2, *args, **kwargs):
    print(a, b, args, kwargs)

f()                  # => 1 2 () {}
f(b=3)               # => 1 3 () {}
f(1,2,3,4,5)         # 1 2 (3, 4, 5) {}
f(1,2,3,4,5,x=6,y=7) # => 1 2 (3, 4, 5) {'x': 6, 'y': 7}
```

As we can see, python has 2 kinds of keyword arguments, the positional arguments can be assigned with a name, like `f(b=3, a=2)`, which is different from the arguments declaration order, this is different from other language like ruby. It is useful while a function have many default arguments, in C, we have to assign from the left, which is not convenient when you just want to change just one argument.
We can't assign positional argument after keyword arguments, like `f(a=1,2)`.

Sometimes there are some required keyword arguments, we can achieve this by
`f(blah, *, req1, req2)`, then `req` must assign explicitly with keyword arguments syntax.

While in ruby, the general arguments format is `f(ps, *args, &block)`.
