---
layout: post
title: reload-dependencies-ipython.md
author: Olivier
tags: [python]
---
Problem : In ipython, the reload of the import is not automatically done when launching new script or launching new command

One simple solution is just to run the 2 following commands :

``` python
%load_ext autoreload
autoreload 2
```

If you want to make this change permanently, you can write in your ipython profile (find it with `ipython locate`).
For instance, if the result of `ipython locate` is "~/.ipython", you can edit "~/.ipython/profile_default/ipython_config.py":
``` python
c = get_config()
c.InteractiveShellApp.extensions = ['autoreload']
c.InteractiveShellApp.exec_lines = ['%autoreload 2']
```
