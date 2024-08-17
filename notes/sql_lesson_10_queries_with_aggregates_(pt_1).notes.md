# SQL Lesson 10: Queries with aggregates (pt. 1)

In addition to simple expressions, SQL also supports aggregate expressions (functions) that can be used to summarise information about a group of rows of data:

```SQL
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, ...
FROM mytable
```

Without a specified grouping, each aggregate function is going to run on the whole set of result rows and return a single value.

## Common aggregate functions
