---
layout: post
title: Create patches from commits and apply them
author: antoine-cha
tags: [git]
---

## Create `.patch` files from commits

```Shell
git format-patch \
    -k \
    -o $OUTPUT_DIR \
    REV1..REV2
```
Creates `.patch` files per commit, the options are:
- `-k`: keep the commit message (do not add `[PATCH]` to it)
- `-o $OUTPUT_DIR`: the patch files are written to this dir
- `REV1..REV2`: commits ranging from `REV1` (excluded) to `REV2` (included) are used to created patches.

### Example
```
git format-patch -k -o my_patches 79bfe71..b83f760
```

## Apply `.patch` files

### Checking for conflicts

You can check that the patch can be safely applied with:
```
git apply --check commit.patch
```
If no output, this can be applied without any conflicts.

### Merging patch

```
git am -3 commit.patch
```
This will apply the patch, adding the commit using the info found in the file to your current history.

In case of conflicts, the same tool as for merge conflicts will be available.
