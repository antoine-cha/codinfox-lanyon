---
layout: post
title: building-tensorflow.md
author: Antoine
tags: [python]
---
## Building Tensorflow from sources


#### Sandbox issue

If the command:
```Shell
bazel build -c opt --config=cuda //tensorflow/cc:tutorials_example_trainer
```

fails with
```
src/main/tools/namespace-sandbox.c:545: mount("none", "/", NULL, MS_REC | MS_PRIVATE, NULL): Permission denied
```

then add the options `--spawn_strategy=stsndalone --genrule_strategy=standalone`

```
bazel build -c opt --config=cuda --spawn_strategy=standalone --genrule_strategy=standalone //tensorflow/cc:tutorials_example_trainer
```

_source: https://github.com/bazelbuild/bazel/issues/418_
