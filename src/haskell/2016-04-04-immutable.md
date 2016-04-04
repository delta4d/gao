---
layout: post
title: "no side effects"
date: 2016-04-04 20:32:16
categories: ["haskell"]
tags: []
---

I finally have some understanding of 'no side effects' in haskell after [lambda calculi march 2016][].

[lambda calculi march 2016]: https://www.hackerrank.com/contests/lambda-calculi-march-2016/challenges

No side effects means if we pass same arguments to same function, we get the
same result. Then if we execute `sqrt 2` 5 times, we got `1.41...` 5 times, but
look, as no side effects indicts, 5 `sqrt 2` all produce the same result, so we
just cache one, we just need to execute only once, and surprisingly, we
don't know which `sqrt 2` execute first!

No side effects means one function can not affect the other one, then why the
execute order bother? So the only order matters is that one function feed then
output to the other. Otherwise, We don't know the execute order of function.
Amazing, huh? And what's more? As they don't effect each other, we just could
do it concurrently. It may be hard in other languages, but it is _natural_ in
functional programming languages.

No side effects means same value constructor with same construct arguments
produce the same value. It is easy to understand, as value constructor is just
a function. There is a great technique in functional programming called _zipper_,
we just need a value to reconstruct the parent node or something else, which
blows my mind when I first saw it. As with lots of C++ experience, `new cls(...)`
can't be the same all the time, right? But haskell does!

I have just thought of these 3, still have much more to learn.
