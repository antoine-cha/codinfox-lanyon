---
layout: post
title: remap_keys.md
author: Olivier
tags: [Olivier,vim]
---
In Vim, the \<ESC> and \<CTRL> keys are hard to reach, but used a lot.

## New way to get out Insert mode
Change the \<ESC> key to `jk`.
It allows efficient escape from Insert mode, as your fingers should already be on `j` and `k` keyboard keys.

In `~/.vimrc`:
```
inoremap jk <ESC>
```


## Remap \<CAPS LOCK> to \<CTRL>
The \<CTRL> key is hard to reach and the \<CAPS LOCK> key is useless.
We have to remap at the system level.
For **Ubuntu 14.04**, modify the `/etc/default/keyboard` file with replacing:
```
XKBOPTIONS=“”
```

with:
```
XKBOPTIONS=“ctrl:nocaps”
```

We then have to restart the computer.  
(cf. [original post](http://askubuntu.com/questions/453793/remapping-caps-lock-in-14-04-trusty-tahr))
