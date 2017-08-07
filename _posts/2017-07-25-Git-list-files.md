---
layout: post
title: git ls-files
comments: true
tags: git
author: klex
---

Show information about files in the index and the working tree.

### List all files in the repository staged
```
git ls-files
```

### List all files in the repository not staged in the index

```
git ls-file -o
```
Useful if you need a clean repository and make a new install.
