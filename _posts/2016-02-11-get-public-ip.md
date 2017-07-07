---
layout: post
title: get-public-ip.md
author: antoan2
tags: [antoan2,bash]
---
# Get the public ip from command line

You want to know what is your public ip from the command line.

You can use one of the following command :

* Command 1. Using wget
```
wget http://ipecho.net/plain -O - -q ; echo
```
* Command 2: Using curl
```
curl ipecho.net/plain; echo
```
* Command 3: Using wget
```
wget http://observebox.com/ip -O - -q ; echo
```
* Command 4: Using curl
```
curl icanhazip.com
```
* Command 5: Using curl
```
curl ifconfig.me
```

src : [5 Commands to Get Public IP using Linux Terminal](http://tecadmin.net/5-commands-to-get-public-ip-using-linux-terminal/)
