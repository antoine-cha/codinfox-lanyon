---
layout: post
title: cp-file-with-directory-structure.md
author: Klexounet
tags: [bash]
---
## Copy a set of files present in a directory in another directory conserving the structure

To want to copy only the `cuts.csv` files from the `processed` directory to the `processed_SD` one, conserving the sub-directory architecture :


```
# In the processed directory
find */interval_0[0-9]/cuts.csv -type f | xargs -i cp "{}" ../processed_SD/ --parents`
```

```
/processed     --------------->    /processed_SD
|
+-- arrow
|    |
|    +-- interval_00
|    |   |
|    |   +-- image.jpg
|    |   +-- cuts.csv
|    |
|    +-- interval_01
|    |   |
|    |   +-- cuts.csv
|    |
|    :
|
+-- game_of_thrones
     |
     +-- interval_00
     |   |
     |   +-- cuts.csv
     :
```
