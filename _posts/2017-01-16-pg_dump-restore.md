---
layout: post
title: pg_dump-restore.md
author: Antoine
tags: [Antoine,sql]
---
# Using `pg_dump` and `pg_restore` to save and reload a PostgreSQL database

Test settings:
- origin DB: PostgreSQL 9.5.5, saving `rcwd` took ~5-10 min for an output file of 1.6G
- destination DB: PostgreSQL 9.4.8, restoring `rcwd` took ~5-10 min for an output file of 1.6G


## Saving the database

```Bash
pg_dump -F tar -f $SAVE_FILE $DB_NAME
```
- `$SAVE_FILE` file to store the output
- `$DB_NAME` db to save
- `-F tar` to save in a tar file

## Restoring the database 

```Bash
pg_restore $SAVE_FILE -d $DB_NAME --clean
```
- `$SAVE_FILE` file to store the output (file format is inferred from the extension
- `--clean` erases the database $DB_NAME before restoring the data (fresh start)


## Useful links

- pg_dump http://docs.postgresql.fr/9.2/app-pgdump.html
- pg_restore http://docs.postgresql.fr/8.1/app-pgrestore.html
