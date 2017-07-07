---
layout: post
title: timing-with-timeit.md
author: Antoine
tags: [Antoine,python]
---
## Timing execution with timeit

Using the module `timeit` we can time the execution of pieces of code, and repeat the process `<number>` times.

Here is an example from the `Reminiz_experiments/datasets/rcmd.py` script:

```Python
import timeit

...RCMD class definition...

def time_func(call, setup, nb_repeat=3):
  t = timeit.timeit(call, setup=setup, number=nb_repeat)
  avg_t = t / nb_repeat
  s = '%.6f s  in average for "%s"' % (avg_t, call)
  return s
if __name__ == "__main__":
  setup = 'from __main__ import RCMD\nrcmd = RCMD()'
  nb_repeat = 3 
  calls_to_time = [ 
    'rcmd.actorToTracks(23)',
    'rcmd.movieToTracks(22)',
    'rcmd.idsToPaths(1)', 
    'rcmd.idsToPaths([1, 1000, 10000, 100000, 1000000, 10000000])',
    'rcmd.trackToIds(155)']
  for call in calls_to_time:
    print(time_func(call, setup, nb_repeat=nb_repeat)) 
```

Output:
```
0.020010 s  in average for "rcmd.actorToTracks(23)"
0.020802 s  in average for "rcmd.movieToTracks(22)"
0.000094 s  in average for "rcmd.idsToPaths(1)"
0.000306 s  in average for "rcmd.idsToPaths([1, 1000, 10000, 100000, 1000000, 10000000])"
1.334021 s  in average for "rcmd.trackToIds(155)"

```
