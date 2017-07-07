---
layout: post
title: sorting-special-chars.md
author: Antoine
tags: [python]
---
### Sorting with special characters

```Python
import PyICU

list = ['é', 'è', 'a', 'b', 'e', 'à']
print(sorted(list))
# >> ['a', 'b', 'e', '\xc3\xa0', '\xc3\xa8', '\xc3\xa9']

COLLATOR = PyICU.Collator.createInstance(PyICU.Locale('fr_FR.UTF-8'))
print(sorted(cmp=COLLATOR.compare))
# >> ['a', '\xc3\xa0', 'b', 'e', '\xc3\xa9', '\xc3\xa8']
```
