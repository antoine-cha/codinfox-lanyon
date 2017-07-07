---
layout: post
title: color-active-tab.md
author: Antoine
tags: [Antoine,bash]
---
## Coloring the active tab

1. Create the file `~/.config/gtk-3.0/gtk.css`

2. Write in it:

```CSS
TerminalWindow .notebook tab:active {
    background-color: #def;
}
```
See [colors in HTML](http://www.w3schools.com/colors/colors_names.asp) for a list of colors.

_source: http://askubuntu.com/questions/40332/how-to-make-selected-tab-in-terminal-more-prominent_
