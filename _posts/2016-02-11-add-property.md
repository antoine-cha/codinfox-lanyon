---
layout: post
title: add-property.md
author: antoan2
tags: [antoan2,oar]
---
# Adding property on ressources

If you want to have some nodes with specific configuration, you can add property that you will specify when using oarsub

* Add string property to the ressources table
```
oarproperty -a yourPropertyName -c
```
* Add property to the node (be careful about the "y")
```
oarnodesetting -a -h '' -p yourPropertyName=y1
```
* Call oarsub like this (be careful about the "missing y")
```
oarsub -I -l "/switch=2/nodes=10+{type='mathlab'}/yourPropertyName=1"
```

src : [Admin FAQ](http://oar.imag.fr/docs/2.5/admin/faq.html)
