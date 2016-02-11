---
layout: post
title: "comma in rake"
date: 2016-02-11 00:35:03
categories: ["ruby"]
tags: []
---

In [rake][rake] passing argument with comma to a task is not what we expected.

```ruby
# Rakefile
task :hello, %i[name] do |t, args|
	puts "hello #{args.name}"
end
```

Then we execute `rake hello['alice,bob']`, we only get `hello alice`.
This is basicly because `,` is used to seperate arguments.

In order to get what we wanted, we can simply escapse comma.
`rake hello[alice\,bob]` gets `hello alice,bob`.

[rake]: https://github.com/ruby/rake
