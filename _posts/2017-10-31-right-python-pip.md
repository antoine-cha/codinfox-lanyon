---
layout: post
title: Right python pip
comments: true
category: python python3 pip pip3
---

## Context
When you install several versions of python on your machine, there might be some mixed issues when using pip.

For example, when using pip3, you see that the requirements are already satisfied, but for python2.7 :
``` bash
tonio@mythe ~ » pip3 install --user neovim
Requirement already up-to-date: neovim in /usr/local/lib/python2.7/dist-packages
```

## Solution

Run the `python -m pip` command to execute the right pip :
```
python -m pip install --user neovim
python3 -m pip install --user neovim
```
