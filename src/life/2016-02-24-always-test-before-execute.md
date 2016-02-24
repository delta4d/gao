---
layout: post
title: "always test before execute"
date: 2016-02-24 11:11:08
categories: ["life"]
tags: []
---

Last week, I start to look some videos grabed from the net, I found the name of
the video is too long, I want to cut the prefix of the name, so I started to
write a ruby script to do such work. But after execution, the videos has left
only one, named 'y'. It turns out I fogot the interpolation, `"mv #{x} y"` should
be "mv #{x} #{y}".

At first I test it without `mv`, and executed in a subfolder, and the result is
ok, then I wrote a script in the root dir, and rewrite the script to do the operation
to all subfolders, this time without testing, it made all the file go away...

ALLWAYS TEST BEFORE DANGEROUS OPERATION
