---
layout: post
title: terminal-encoding.md
author: Antoine
tags: [docker]
---

## CLI

```bash
$ vim *.py
# This opens the files in their own tabs.

$ vim -o *.py
# This opens the files in horizontal splits.

$ vim -O *.py
# This opens the files in vertical splits.
```

## From vim 

```vim
:args *.py | all
# This opens the files in horizontal splits.

:args *.py | vertical all
# This opens the files in vertical splits.
```

