---
layout: post
title: "user-defined conversion"
date: 2016-02-11 11:26:16
categories: ["cpp"]
tags: []
---

We can define our own type conversion for ADT in c++ with syntax like
`operator TYPE() const {...}`. Such as the following meaning code.

```cpp
struct Complex {
	operator string() const { return to_string(x) + " " + to_string(y); }
	explicit operator int() const { return x; }
	Complex(int x=0, int y=0):x(x), y(y) {}
	int x, y;
};

int main() {
	Complex x(1, 2);
	string sx = x;

	cout << string(x) << endl; // explicit conversion
	cout << sx << endl;        // implicit conversion
	cout << int(x) << endl;
	// int rx = x;
	// cout << rx << endl;
	//! ERROR can not implicit conversion
	return 0;
}
```

Since c++11, we can use explicit qualifier to force the type conversion to be
explicit.

---

1. http://en.cppreference.com/w/cpp/language/cast_operator
