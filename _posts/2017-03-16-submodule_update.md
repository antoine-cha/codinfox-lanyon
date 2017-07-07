---
layout: post
title: submodule_update.md
author: Klexounet
tags: [Klexounet,git]
---
## Submodule update

Api is a submodule of VoD.

#### `git submodule update <path/to/the/submodule>`

Reset submodules at the commit where they were at the last commit of the superproject. In case of no submodule is provided, apply the command to each one.

![alt tag](https://github.com/antoan2/Reminiz_sysadmin/blob/master/tips/git/images/submodules_0.png)

#### `git submodule update --remote <path/to/the/submodule>`

Pull the submodules at HEAD stated in .gitmodules.

![alt tag](https://github.com/antoan2/Reminiz_sysadmin/blob/master/tips/git/images/submodules_1.png)

## New commit in superproject

After a `git submodule update --remote`, when you're in state V0 / HEAD, you create a new commit of the superproject.
This creates a new commit, and associate the commit hashes of the submodules currently used.

![alt tag](https://github.com/antoan2/Reminiz_sysadmin/blob/master/tips/git/images/submodules_2.png)
