---
layout: post
title: Setting up automatic vacuum and analyze
tags: [psql]
author: klex
---

[Source: Lob's blog](https://lob.com/blog/supercharge-your-postgresql-performance)

Some time, when the tables get bigger, the request time of some requests can be incredibly high (5 minutes for a join on a table).
The explaination can come from the tables not being properly vacuumed or analyzed.

> **Vacuuming** cleans up stale or temporary data, and **analyzing** refreshes its knowledge of all the tables for the query planner. We saw an immediate decrease in execution time for our complex queries, and as a result, a much more user-friendly internal website.

## Diagnostic
To see the last time the tables has been vaccumed and analyzed
```
SELECT relname, last_vacuum, last_autovacuum, last_analyze, last_autoanalyze
FROM pg_stat_all_tables WHERE schemaname = 'public';
```

## Single shot vacuum
```
VACUUM ANALYZE table_name;
```

## Set-up automation
```
ALTER TABLE table_name SET (autovacuum_vacuum_scale_factor = 0.0);
ALTER TABLE table_name SET (autovacuum_vacuum_threshold = 5000);
```
Tables are auto-vacuumed when the number of row inserted is greater than the corresponding threshold
```
vacuum threshold = autovacuum_vacuum_threshold + autovacuum_vacuum_scale_factor * number of rows in table  
```
