---
layout: post
title: defaultdict.md
author: Antoine
tags: [Antoine,python]
---
## Default dicts in Python

- Initialize the values with predefined element upon calling the key.

```Python
from collections import defaultdict

# Basic
d = defaultdict(int)
d['a']
>> 0

d = defaultdict(list)
# This does not fail with a defaultdict
d['a'].append('coucou')
d['a']
>> ['coucou']

# Advanced 
d = defaultdict(lambda: {'state': 4, 'weather': 'sunny'})
d['a']
>> {'state': 4, 'weather': 'sunny'}
```


