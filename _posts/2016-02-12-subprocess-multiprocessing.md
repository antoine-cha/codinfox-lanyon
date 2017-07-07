---
layout: post
title: subprocess-multiprocessing.md
author: Antoine
tags: [Antoine,python]
---
### Using subprocesses with multiprocessing

When using multiprocessing, os.system calls may not be killed on `Ctrl+C`. Instead, use `subprocess.call(<command>)`.

```Python
import multiprocessing as mp
import subprocess
import time

def wait(i):
    subprocess.call('sleep %d' % i, shell=True)
    print(i)
    return i

pool = mp.Pool(processes=4)
x = range(4)
start = time.time()
try:
    pool.map(wait, x, 1)
finally:
    pool.close()
    pool.join()
duration = time.time() - start
print('Done in %.2f s' % duration)
```
will output
```
0
1
2
3
Done in 3.0 s
```

