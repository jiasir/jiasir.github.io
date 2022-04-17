---
title: "How Python Decorator Works"
date: 2017-03-16
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["Python"]
tags: ["Python"]
description: "Decorators provide a simple syntax for calling higher-order functions. A decorator is a function that takes another function and extends the behavior of the latter function without explicitly modifying it."
---

Decorators provide a simple syntax for calling higher-order functions. A decorator is a function that takes another function and extends the behavior of the latter function without explicitly modifying it.

### How function works
Functions return a value based on the given arguments.
```python
def foo(bar):
    return bar + 1
print(foo(2)) # will print 3
```

### What is first class object
All objects that could be named in the language (e.g., integers, strings, functions, classes, modules, methods, etc.) to have equal status. That is, they can be assigned to variables, placed in lists, stored in dictionaries, passed as arguments, and so forth. That were "first class".
```python
def foo(bar):
    return bar + 1
print(foo) # will print <function foo at 0x100ec1488>
print(foo(2)) # will print 3
print(type(foo)) # will print <type 'function'>
def call_foo(foo, arg):
    return foo(arg)
print(call_foo(foo, 3)) # will print 4
```

### Nested Functions
This example shows the child functions are not available outside of the parent function.
```python
def parent():
    print("Printing from the parent() function.")
    def child_1():
        return "Printing from the child_1() function."
    def child_2():
        return "Printing from the child_2() function."
    print(child_1())
    print(child_2())
```
When you calling the `parent()` function, you should get that messages. But try calling the `child_1()` or `child_2()` function, you should get an error.

### Returning Functions
Python also allows you to return functions from other functions.
```python
def parent(num):
    def child_1():
        return "Printing from the child_1() function."
    def child_2():
        return "Printing from the child_2() function."
    try:
        assert num == 10
        return child_1
    except AssertionError:
        return child_2
foo = parent(10) # variable foo is the same as child_1
bar = parent(11) # variable bar is the same as child_2
print(foo) # output: <function child_1 at 0x100ec1578>
print(bar) # output: <function child_2 at 0x100ec15f0>
print(foo()) # output: Printing from the child_1() function.
print(bar()) # output: Printing from the child_2() function.
```

### Decorators
Now, that's show the decorators examples.
```python
def my_decorator(f):
    def wrapper():
        print("Something is happening before f() is called.")
        f()
        print("Something is happening after f() is called.")
    return wrapper
def my_function():
    print("Calling my_function!")
my_function = my_decorator(my_function) # my_function is the same as wrapper
my_function() # my_function is the same as wrapper()
```

Output:
```
Something is happening before f() is called.
Calling my_function!
Something is happening after f() is called.
```

We can using the syntactic sugar `@` symbol instead of variable assignment:
```python
def my_decorator(f):
    def wrapper():
        print("Something is happening before f() is called.")
        f()
        print("Something is happening after f() is called.")
    return wrapper
@my_decorator # the same as my_function = my_decorator(my_function)
def my_function():
    print("Calling my_function!")
my_function() # my_function is the same as wrapper()
```
`@my_decorator` is just an easier way of saying `my_function = my_decorator(my_function)`.

Output:
```
Something is happening before f() is called.
Calling my_function!
Something is happening after f() is called.
```

Let's try another example. This decorator is used for rate limiting. Test it out.
```python
from time import sleep
def sleep_decorator(f):
    """
    Limits how fast the function is
    called.
    """
    def wrapper(*args, **kwargs):
        sleep(2)
        return f(*args, **kwargs)
    return wrapper
@sleep_decorator
def print_number(num):
    return num
print(print_number(1))
```
This will sleep two seconds and print 1.

And the example shows decorator with arguments:
```python
def my_decorator(name=None):
    def upper(f):
      def inner(*args, **kwargs):
        #do something
         return f(*args, **kwargs)
      return inner
    return upper
@my_decorator(name="jiasir") # the same as my_function = my_decorator(name="jiasir")(my_function)
def my_function(num):
    print("Calling my_function! Num: %s" % num)
my_function(1) # the same as my_decorator(name="jiasir")(my_function)(1)
```
Output:
```
Calling my_function! Num: 1
```