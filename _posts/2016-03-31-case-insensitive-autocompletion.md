---
layout: post
title: case-insensitive-autocompletion.md
author: antoan2
tags: [antoan2,bash]
---
Problem : can be cool to autocomplete "doc[tab]" even if the folder is named "Documents"
Goal : We are going to modify .inputrc

Setup :
- check if you already have a .inputrc in your home (if not create it)
- add the following line :
```
set completion-ignore-case On
```
- open new terminal, should be ok
