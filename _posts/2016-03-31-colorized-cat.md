---
layout: post
title: colorized-cat.md
author: antoan2
tags: [bash]
---
Problem : It can be cool to have some syntax color highlight when quickly checking the content of a file with "cat"
Goal : We are going to use pigmentize and create an alias called "pcat" (pygmentized cat)

Setup :
- install pigmentize
``` bash
sudo apt-get install python-pygments
```
- open your bashrc and add the line "alias pcat='pygmentize -g'"
- source your bashrc (source ~/.bashrc)
- you can now use the following cmd : "pcat filename"
