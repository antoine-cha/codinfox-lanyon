---
layout: post
title: Removing_spaces.md
author: Klexounet
tags: [Klexounet,vim]
---
Add an auto regex to your `~/.vimrc`, so that each time you write a file with vim (`:w` or `:x`), it deletes all the useless spaces at the end of the lines.

```
" Remove useless spaces at the end of the line
autocmd BufWritePre * %s/\s\+$//e
```
