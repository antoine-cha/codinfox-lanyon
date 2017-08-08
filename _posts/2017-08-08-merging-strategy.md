---
layout: post
title: Merging strategy
author: antoine-wdg-rmz
tags: [git]
---

When wanting to merge branch `feature-x`:

```bash
git checkout feature-x
git fetch origin
git rebase origin/develop [-i]
git push origin feature-x [-f]
```

Then:
- open a PR on Bitbucket
- merge and **force a merge commit** (when merging manually,
go to `develop` branch and `git merge feature-x --no-ff`)
