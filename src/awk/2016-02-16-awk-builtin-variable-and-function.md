---
layout: post
title: "awk builtin variable and function"
date: 2016-02-16 17:32:13
categories: ["awk"]
tags: []
---

|var or func|meaning|
|-----------|-------|
|ARGC|argument count|
|ARGV|argument vector|
|FILENAME|att|
|FNR|record number in *current* file|
|NF|number of fields|
|NR|number of records so far|
|FS|field separator, default to blank|
|OFMT|output format for numbers|
|OFS|output field separator|
|ORS|output record separator|
|RS|record separator|
|RSTART|start of string matched by `match`|
|RLENGTH|length of string matched by `match`|
|SUBSEP|subscript separator|
|BEGIN|special pattern, match before first line|
|END|special pattern, match after last line|
|atan2(y,x)|arctangent of y/x from -pi to pi|
|cos(x)|cosine, with x in radians|
|exp(x)|expoential|
|int(x)|integer part of x|
|log(x)|logarithm with base *e*|
|rand()|random number generator, with range [0,1)|
|sin(x)|sine, with x in radians|
|sqrt(x)|square root|
|srand(x)|set rand() new seed x|
|gsub(r,s, t=$0)|substitute s for r globally in string t|
|index(s,t)|return first position of string t, 0 if not found|
|length(s)|number of chars in string s|
|match(s,r)|test whether s contains a substring matched by r|
|split(s,a,fs=FS)|split s into array a on field separator fs|
|sprintf(fmt,expr-list)|expr-list formated by fmt|
|sub(r,s,t=$0)|substitute s for the leftmost longest substring of t matched by r, return index|
|substr(s,p,n=length(s[p:-1]))|substring of lenght n starting at p|
