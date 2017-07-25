# Show information about files in the index and the working tree of a git repository

In a git repository
```
git ls-files
```
has a bunch of cool options. For example, 
```
git ls-file -o
```
lists all files in the repository not staged in the index, so you can delete them to have a clean repository and make a new install.
