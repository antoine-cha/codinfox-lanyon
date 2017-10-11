---
layout: post
title: SSH config
comments: true
category: Misc
tags: ssh
---

This tip has three goals:
- make ssh command shorter (`ssh klex` instead of `ssh alexandre@father3.reminiz`)
- avoid having to type password when using ssh
- forward you ssh keys so that you can use them while on another machine

## Config file

```
Host klex
    HostName father3.reminiz
    User alexandre
    ForwardAgent yes

Host chacha
    HostName father2.reminiz
    User antoine
    ForwardAgent yes
```

Write this to `.ssh/config`.


## Allow your ssh key on remote machines

For each machine you want to access, run the following command:

```bash
ssh-copy-id -i <path-to-my-key> <host>
```

In our case:

```bash
ssh-copy-id -i ~/.ssh/id_rsa klex
ssh-copy-id -i ~/.ssh/id_rsa chacha
```


## Check that agent forwarding works

SSH on one machine, and type SSH on one machine, and type `ssh -T git@github.com`, this should show you 
your Github username and not the host's one.
If this does not work, go back on your machine and type `ssh-add -L`, if you get `no identity is available`, try 
`ssh-add .ssh/id_rsa` and it should now work.
