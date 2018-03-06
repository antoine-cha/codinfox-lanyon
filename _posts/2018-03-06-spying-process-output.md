---
layout: post
title: Spying process output by PID
comments: true
category: Misc
tags: linux
---

To spy the `stdout` and `stderr` of a process, run:

```bash
sudo strace -s9999 -e write -p <PID>
```

This can be useful when a script is not run by you and you want to get the `stderr`.
