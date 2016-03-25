---
layout: post
title: "each with index"
date: 2016-03-25 09:28:04
categories: ["python"]
tags: []
---

The first thing in using a new language, is always want something from the other
languages you used to. Such as missing `each_with_index` in python, which is common in ruby.
In python, we should use `enumerate` to get the index.

```python
xs = [1, 2, 3]
for i, x in enumerate(xs):
    print(i, x)
```

As in ruby, we have `xs.each_with_index { |x, i| puts "#{i} #{x}" }`.

The fancy part is ruby use code block to achieve this, python use generator to achieve this, and they both have the keyword `yield`, though they have different semantic meaning.

In ruby, you yield something, which means you throw it to a code block, which user could catch it, and deal it with some code, such as `puts "#{i} #{x}"`.

In python, as long as you have `yield`, then you become a generator, then it could be used in the context `for ... in ...`.

OK, let's achieve this manually.

```ruby
# ruby
Array.class_eval do
    def each_with_index_
        i = 0
        self.each do |x|
            yield x, i
            i += 1
        end
    end
end

xs = [1, 2, 3]
xs.each_with_index_ { |x, i| puts "#{i} #{x}" }
```

```python
# python
def enumerate_(xs):
    i = 0
    for x in xs:
        yield (i, x)
        i += 1

xs = [1, 2, 3]
for i, x in enumerate_(xs):
    print(i, x)
```

As long as I started using python more often, I am surprised that python
sometimes seems so "simple". If you have blah blah method, then you can be
used in blah blah context, seems like duck type, :).
