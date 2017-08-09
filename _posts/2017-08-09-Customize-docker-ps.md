---
layout: post
title: Customize docker ps
author: antoine-cha
tags: [docker]
---

### Default

```
$ docker ps

CONTAINER ID        IMAGE                                                      COMMAND                  CREATED     
     STATUS                    PORTS                                      NAMES                                     
6f29940424f4        mxnet:compile                                              "entrypoint.sh"          21 hours ago
     Up 21 hours                                                          mxnet_compile_1                           
```
With a terminal too small, the output spans 2 lines


### Customized

#### Ephemeral change

```
$ docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Image}}"

NAMES                                 STATUS                    IMAGE        
mxnet_compile_1                       Up 21 hours               mxnet:compile
```

#### Permanent changes

Write in your `~/.docker/config.json`:
```JSON
{
    "psFormat": "table {{.Names}}\t{{.Status}}\t{{.Image}}"
}
```

For more information check https://docs.docker.com/engine/reference/commandline/ps/#formatting
