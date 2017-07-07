---
layout: post
title: set-tab-title.md
author: Antoine
tags: [Antoine,bash]
---
## Set the title of tabs in the terminal 

Add the following function to your `.bashrc`:
```Shell
function set-title() {
  if [[ -z "$ORIG" ]]; then
    ORIG=$PS1
  fi
  TITLE="\[\e]2;$@\a\]"
  PS1=${ORIG}${TITLE}
}
```

Then you can change the name of a tab using `set-title <my title>`. It supports spaces in titles.

_source: http://unix.stackexchange.com/questions/177572/how-to-rename-terminal-tab-title-in-gnome-terminal_
