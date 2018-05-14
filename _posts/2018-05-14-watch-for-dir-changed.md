---
layout: post
title: Watching (and reacting) to changes in a directory
comments: true
tag: [bash,linux]
---

## Watching for changes on a list of file

`entr` is a Linux command to watch a list of files

```bash
# Watch a list of python files and restart server on changes
find ./ -name "*.py" | entr python app.py
```

- Caveat : this does not react on new files.

## Watching for changes and new files in existing dirs

```bash
# Watch a dir and restart server on changes and new files in existing dirs
while true
do 
    find . -name "*.py" | entr -d python ./app.py 
done
```

- The `-d` option stops makes `entr` exit on new files, so the list of files to watch is recomputed.
- Caveat : this does not watch new directories !
