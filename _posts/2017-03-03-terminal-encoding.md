---
layout: post
title: terminal-encoding.md
author: Antoine
tags: [Antoine,docker]
---
## Setting the terminal encoding

- To avoid errors when printing special characters, we need a terminal that supports printing UTF-8 characters.

### Default behaviour

Using a simple Dockerfile

```Dockerfile
FROM ubuntu
RUN apt-get update
RUN apt-get install -y --no-install-recommends \
    python-dev
```

Now attached to the docker
```Shell
root@7ec9e210dbdd$ locale

LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

root@50327e3b3d41$ python -c "print u'\xff'"

Traceback (most recent call last):
  File "<string>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode character u'\xff' in position 0: ordinal not in range(128)
```
The current terminal encoding cannot print non-ASCII characters

### With UTF-8 encoding

Add the following lines to the Dockerfile
```Dockerfile
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8      
ENV LANGUAGE en_US.UTF-8  
ENV LC_ALL en_US.UTF-8    
```
This sets the terminal encoding to UTF-8 (and other things).

```Shell
root@6669fd6259de$ locale

LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

root@6669fd6259de$ python -c "print u'\xff'"

ÿ

``` 
