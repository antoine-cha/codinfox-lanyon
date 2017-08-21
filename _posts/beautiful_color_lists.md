---
layout: post
title: Beautiful color lists
comments: true
tags: colors
author: klex
---

Create easily a list of distinct colors (for plotting or visualisation), using matplotlib.pyplot colormaps

### Get the color list (RGB)

To get a list of colors, go chose the colormap you want [here](https://matplotlib.org/examples/color/colormaps_reference.html).
Multiple shading offs are provided, as well as discrete colormaps (qualitative section).

![beautiful_colormaps](https://matplotlib.org/mpl_examples/color/colormaps_reference_04.png)


You can then create `n` different colors by passing a list of `n` float uniformly spaced between 0 and 1.

### Example

Here, get the 8 colors from Dark2 colormap :
```
import matplotlib.pyplot as plt
COLORS = plt.cm.Dark2(np.linspace(0, 1, 8))
```
