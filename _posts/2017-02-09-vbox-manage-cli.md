---
layout: post
title: vbox-manage-cli.md
author: lcaminon
tags: [bash]
---
List all VMs :

    VBoxManage list vms

launch vms:

    VBoxManage startvm --type headless [vm_id ...]

List all running vms:

    VBoxManage list runningvms

Save and stop vm:

    VBoxManage controlvm vm_id savestate

