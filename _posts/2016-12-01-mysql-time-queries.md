---
layout: post
title: mysql-time-queries.md
author: Antoine
tags: [Antoine,sql]
---
## Timing queries with MySQL

```SQL
mysql> SET profiling = 1;

mysql> SELECT batch.rank, celebrity.name from batch, celebrity WHERE batch.celebrity_id = celebrity.id;
...

mysql> SELECT batch.rank, celebrity.name from batch INNER JOIN celebrity ON batch.celebrity_id = celebrity.id;
...

mysql> SHOW PROFILES;
+----------+------------+--------------------------------------------------------------------------------------------------------+
| Query_ID | Duration   | Query                                                                                                  |
+----------+------------+--------------------------------------------------------------------------------------------------------+
|        1 | 0.30346450 | SELECT batch.rank, celebrity.name from batch, celebrity WHERE batch.celebrity_id = celebrity.id        |
|        2 | 0.17916075 | SELECT batch.rank, celebrity.name from batch INNER JOIN celebrity ON batch.celebrity_id = celebrity.id |
+----------+------------+--------------------------------------------------------------------------------------------------------+
2 rows in set, 1 warning (0.00 sec)

mysql> SET profiling = 0;

```
