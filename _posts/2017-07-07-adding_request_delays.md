---
layout: post
title: adding_request_delays.md
author: antoine-wdg-rmz
tags: [antoine-wdg-rmz,docker]
---
Can be useful when porgramming JS so that the UI is resilient to slow requests.

In one line:

```bash
docker run -v /var/run/docker.sock:/var/run/docker.sock gaiaadm/pumba pumba netem --tc-image gaiadocker/iproute2 -d 24h delay -t 100  <docker_container_name>
```

This adds a 100ms delay on **every packet** for the chosen container.

`<docker_container_name>` can be a regexp by prefixing with `re2:`.
For example to add delay to all containers prefixed with `nlpnertoolbox`:

```
docker run -v /var/run/docker.sock:/var/run/docker.sock gaiaadm/pumba pumba netem --tc-image gaiadocker/iproute2 -d 24h delay -t 100  re2:^nlpnertoolbox
```

More doc on the [github README](https://github.com/gaia-adm/pumba#usage). `pumba` can actually be used for much 
more than just delay.
