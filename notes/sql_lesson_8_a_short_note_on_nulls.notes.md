# SQL Lesson 8: A short note on `NULL`s

Its generally best to avoid `NULL` values where possible in a database because the value requires special attention when constructing queries, constraints, and when processing the results.

An alternative to `NULL` values is to assign data-type appropriate default values, like 0 for numerical data. But when a database can store incomplete data, `NULL` values may be appropriate.

When doing complex queries such as `OUTER JOINS`, `NULL` values may need to be taken into consideration:

```SQL
SELECT column, another_column, ...
FROM mytable
WHERE column IS/IS NOT NULL
```