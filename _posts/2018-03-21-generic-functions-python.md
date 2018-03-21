---
layout: post
title: Generic functions in Python
comments: true
tag: [python3]
---

## Definition

A generic function is a function defined for polymorphism.

## Implementation

In Python3.6, you can achieve this using `functools.singledispatch`:

```python
from functools import singledispatch

@singledispatch
def myfunc(arg, verbose=False):
  if verbose:
    print('Length of strings')
  print('This is not a string')
 
@myfunc.register(str)
def _(arg, verbose=False):
  print(len(arg))
  
 
print(myfunc(3))
# >> 'This is not a string'

print(myfunc('abc'))
# >> 3
```
