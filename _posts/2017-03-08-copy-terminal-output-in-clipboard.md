---
layout: post
title: copy-terminal-output-in-clipboard.md
author: Klexounet
tags: [Klexounet,bash]
---
To copy the output of a command directly into clipboard, without having to select it manually, add 

```<some_command> | xclip -sel clip```

at the end of the command. You can then paste the content !

Example : to copy the SSH key `cat ~/.ssh/id_rsa.pub | xclip -sel clip`
