---
layout: post
title: "rake get caller dir"
date: 2016-05-26 22:28:25
categories: ["ruby"]
tags: []
---

If you execute a rake command, rake will search the current directory for
Rakefile, if not found, rake will search for the parent directory, and repeat
the process until reach the root directory or find the Rakefile.

If you want to know where called rake, you can use `Rake.original_dir` to get it.

See Rake's author, Jim's answer: https://www.ruby-forum.com/topic/93803#189992
