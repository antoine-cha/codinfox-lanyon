---
layout: post
title: put-nodes-alive.md
author: antoan2
tags: [antoan2,oar]
---
# Setting nodes to alive

All your nodes are suspected because you are still in a prototyping phase

Just simple command for loop :
```bash
for i in $(seq 1 6); do sudo oarnodesetting -r $i -s Alive; done
```
