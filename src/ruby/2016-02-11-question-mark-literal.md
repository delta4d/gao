---
layout: post
title: "question mark literal"
date: 2016-02-11 20:06:03
categories: ["ruby"]
tags: []
---

Question mark literal can easily create a string with single char.

I first saw it in a bencode library[^1].

```
>> ?a.class
String
>> ?a
"a"
>> ?\n
"\n"
>> ?\s
" "
>> ?ab
SyntaxError: unexpected '?', expecting end-of-input
>> ?あ
"あ"
```

See ruby-doc[^2] for more details.



[^1]: https://github.com/dasch/ruby-bencode/blob/master/lib/bencode/parser.rb#L19

[^2]: http://ruby-doc.org/core-2.3.0/doc/syntax/literals_rdoc.html#label-Strings
