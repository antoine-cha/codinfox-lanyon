---
layout: post
title: Merging strategy
author: antoine-wdg-rmz
tags: [git]
---

### 1. Rebase branch `feature-x`

```bash
git checkout feature-x
git fetch origin
git rebase origin/develop [-i]
git push origin feature-x [-f]
```

### 2. Merge branch `feature-x`

- open a PR on Bitbucket
- merge and **force a merge commit**
  - when merging manually, go to `develop` branch and `git merge feature-x --no-ff`
