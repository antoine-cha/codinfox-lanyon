---
layout: post
title: SSH config
comments: true
category: Misc
tags: ssh
---

This tip has three goals:
- make ssh command shorter (`ssh alex` instead of `ssh alex@alexComputer`)
- avoid having to type password when using ssh
- forward you ssh keys so that you can use them while on another machine

## Config file

```
Host alex
    HostName alexComputer
    User alex
    ForwardAgent yes

Host nick
    HostName nickComputer
    User nick
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
ssh-copy-id -i ~/.ssh/id_rsa alex
ssh-copy-id -i ~/.ssh/id_rsa nick
```

**Note:** since `~/.ssh/id_rsa` is actually the default path for the ssh key, we can just use `ssh-copy-id <host>`

## Check that agent forwarding works

SSH on one machine, and type SSH on one machine, and type `ssh -T git@github.com`, this should show you 
your Github username and not the host's one.
If this does not work, go back on your machine and type `ssh-add -L`, if you get `no identity is available`, try 
`ssh-add .ssh/id_rsa` and it should now work.
