---
layout: post
title: find-and-execute-them-all.md
author: lcaminon
tags: [bash]
---
Problem : You want to execute the same command into a lot of subdirectories ?

Goal : We are going to use find

Search your files with find like this :

    find . -name "fileToBeFound"

and add your command ({} is the path to the occurence of the file found)!

    find . -name "fileToBeFound" -exec the command to execute {} \;

Note you can use wildcards to search file, add more than one directory, search by type (directory, file ...)