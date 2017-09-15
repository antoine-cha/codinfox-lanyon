---
layout: post
title: Iterating by chunks of same size 
author: antoine-cha
tags: [python]
---


## Formula
```python
>> L = range(10)
# We want [(0, 1, 2), (3, 4, 5), (6, 7, 8)]
>> zip(*[iter(L)]*3)
[(0, 1, 2), (3, 4, 5), (6, 7, 8)]
```

## Explanations

### Creating the object to iterate over
- `iter(L)`: `iter` returns an iterator over its argument (https://docs.python.org/2/library/functions.html#iter)
- `[obj] * N` returns a list of N __references__ to `obj`. 
  - If `obj` is a dict, modifying the first element of the list will affect all the other elements of the list.

```python
>> L = range(10)
>> M = [iter(L)]*3
>> M[0].next()
0
>> M[1].next()
1
>> M[0].next()
2
```
[Docs for `next`](https://docs.python.org/2.7/library/stdtypes.html#iterator.next)

### `*` operator

- The `*` operator is used to unpack an array into positional arguments for a function
- From the [docs](https://docs.python.org/2.7/tutorial/controlflow.html#unpacking-argument-lists):
 ```python
>> range(3, 6)      # normal call with separate arguments
[3, 4, 5]
>> args = [3, 6]
>> range(*args)     # call with arguments unpacked from a list
[3, 4, 5]
 ```

### `zip`

- From the [docs](https://docs.python.org/2/library/functions.html#zip):
  - `zip` returns a list of tuples. The i-th tuple contains the i-th element from each of the argument sequences or iterables.
```python
>> x = [1, 2, 3]
>> y = [4, 5, 6]
>> zipped = zip(x, y)
>> zipped
[(1, 4), (2, 5), (3, 6)]
```

### All together

```python 
>> L = range(10); print(L)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>> it = iter(L); print(it)
<listiterator object at 0x7f90600880d0>
>> M = [it, it, it]; print(M)
[<listiterator object at 0x7f90600880d0>, <listiterator object at 0x7f90600880d0>, <listiterator object at 0x7f90600880d0>]
>> zip(*M)
[(0, 1, 2), (3, 4, 5), (6, 7, 8)]
```

## Improvement

- The last element of L (9) is not in the result:
  - `zip` stops upon reaching the 1st empty iterable
- To obtain the last elements, use [`itertools.izip_longest`](https://docs.python.org/2/library/itertools.html#itertools.izip_longest)
  - As [`izip`](https://docs.python.org/2/library/itertools.html#itertools.izip), this returns an iterator, not a list
  
```python
>> import itertools
>> L = range(10)
# We want [(0, 1, 2), (3, 4, 5), (6, 7, 8)]
>> for e in itertools.izip_longest(*[iter(L)]*3):
>>     print(e)
(0, 1, 2)
(3, 4, 5)
(6, 7, 8)
(9, None, None)
```
