---
layout: post
title: "select m from n randomly"
date: 2016-04-10 00:31:53
categories: ["algo"]
tags: []
---

```
choose 0 _ = []
choose _ [] = []
choose m (x:xs) | rand len < m = m : choose (m-1) xs
                | otherwise    = choose m xs
              where len = length xs + 1
```

OK, the algorithm is very clear, the problem is to select m from n elements,
first, consider the first element, we have m/n probability to choose it, if
choose it, the problem reduces to select m-1 from n-1 elements, otherwise,
select m from n-1 elements.

This a classic solution, but I just understand it recently. What I first thought
is we select with `n/k`, then if not selected, then as second one should also be
selected with probability n/k, then we have `(1-n/k)\*x=n/k`, so we should selected
second element now with probability `x`, which is absurd.

The element are all individually selected, they don't affect each other, thus
`x` is wrong.

I always thought I finally understand something, but it always turns out
that I don't understand it at all.

In recent years, I find myself can hardly think a question, I always don't know
what to do, but the solution always turns out to be simple and clear. The way
I am thinking is a big problem now.

Stupid, stupid me.
