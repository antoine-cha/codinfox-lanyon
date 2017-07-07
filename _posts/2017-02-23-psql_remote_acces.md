---
layout: post
title: psql_remote_acces.md
author: Antoine
tags: [sql]
---
# Allow remote access from a specific adress

## Grant access to a remote host

Error looks like `FATAL:  no pg_hba.conf entry for host "90.43.68.153", user "django", database "rcwd", SSL off`.

Modify the file `/etc/postgresql/<postgre_version>/main/pg_hba.conf`:
- After the lines 
```
# This file controls: which hosts are allowed to connect, how clients
# are authenticated, which PostgreSQL user names they can use, which 
# databases they can access.  Records take one of these forms:       
#                                                                    
# local      DATABASE  USER  METHOD  [OPTIONS]                       
```
- Add an host as:
```
host      all all 90.43.68.153/32 md5
```
For instance, this will allow access from all Azure machines in our group rcwd:
```
host      all all 172.22.0.0/24 md5
```

__Warning:__ 

- If you set the method to `trust`, Postgre won't need passwords.
- If you set the method to `password`, Postgre sends password in clear text.

## Reload PostgreSQL confs

PostgreSQL is presumably running as an upstart job, you can check that with:
```
service postgresql status
```
If it is up and running, you can reload the conf by
```
service postgresql reload
```

