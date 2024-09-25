# SQL Lesson 10: Queries with aggregates (pt. 1)

In addition to simple expressions, SQL also supports aggregate expressions (functions) that can be used to summarise information about a group of rows of data:

```SQL
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, ...
FROM mytable
```

Without a specified grouping, each aggregate function is going to run on the whole set of result rows and return a single value.

## Common aggregate functions

The following are common SQL aggregate functions:

- `COUNT(*)`, `COUNT(column)`: Count the number of rows in the group of no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column.
- `MIN(column)`: Finds the smallest numerical value in the specified column for all rows in the group.
- `MAX(column)`: Finds the largest numerical value in the specified column for all rows in the group.
- `AVG(column)`: Finds the average numerical value in the specified column for all rows in the group.
- `SUM(column)`: Finds the sum of all numerical values in the specified column for all rows in the group.

## Grouped aggregate functions

In addition to aggregating across all rows, you can also apply the same aggregate functions to individual groups of data using the `GROUP BY` clause:

```SQL
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression
GROUP BY column;
```

The `GROUP BY` clause works by grouping rows that have the same value in the column specified.
