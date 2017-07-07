---
layout: post
title: linked_figure_reference.md
author: Antoine
tags: [Antoine,latex]
---
To link a figure in a latex document :

\usepackage{hyperref}
...
\hyperref[fig:label]{Figure \ref*{fig:label} }

Then, when clicking on the "Figure N" text, it will send you to the caption of the figure.

You can add 

\usepackage[all]{hypcap}

And it will send you to the top of the figure.
