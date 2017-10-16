---
layout: post
title: Create a patch from a pull request
author: Klex
tags: [bitbucket git]
---

## Bitbucket: create a git patch from a pull request

To create a patch from a pull request, so that the branch can be deleted, and the changes can be merged later if needed

```
curl -u user:password https://bitbucket.org/api/2.0/repositories/{user}/{repo}/pullrequests/{pull_no}/patch -L -o name.patch
```
You can then link the `.patch` file in a new pivotal ticket for example.

To apply the patch later, simply use

```
git apply name.patch
```


[Reference](https://bitbucket.org/site/master/issues/8323/add-link-for-raw-patch-to-pull-request-ui#comment-6590315)
