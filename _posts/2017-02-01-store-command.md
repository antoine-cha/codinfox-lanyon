---
layout: post
title: store-command.md
author: Antoine
tags: [Antoine,bash]
---
# Storing a command in a var to evaluate it whenever needed

```Shell
# Store the cmd
CMD="wc -l a.txt"
touch a.txt
echo $CMD
# >> wc -l a.txt
# The result of the command is obtained using 
echo `eval $CMD`
# >> 0 a.txt
echo "Hello !" >> a.txt
echo `eval $CMD`
# >> 1 a.txt
```
__WARNING:__ in the terminal, `$CMD` returns the result of the command, use `echo $CMD` to get the command.
