---
layout: post
title: cheatsheet.md
author: antoan2
tags: [docker]
---
# Remove all stopped containers.
```
docker rm $(docker ps -a -q)
```

# Remove all untagged images
```
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
```

# Exiting docker container without killing it
- run docker container in detach mode "-d"
- attach container
- ctrl p + ctrl q
