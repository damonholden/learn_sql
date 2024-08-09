# SQL Lesson 7: `OUTER JOIN`s

With `INNER JOIN`, the resulting table only contains data that exists in both tables.

If two tables have asymmetric data, which can easily happen when data is entered in different stages, then `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` can be used to make sure data from either table is not left out:

```SQL
SELECT column, another_column, ...
FROM mytable
INNER/LEFT/RIGHT/FULL JOIN another_table
	ON mytable.id = another_table.matching_id
```

Just like `INNER JOIN`, these three `OUTER JOIN`s have to specify which columns to join the data on.

When joining two tables (table A and table B):

- `LEFT JOIN` will include all rows from table A regardless of where there is a matching row in table B.
- `RIGHT JOIN` is the same as `Left JOIN`, but reversed.
- `FULL JOIN` keeps all rows from both tables, regardless of matching rows from each other.

When using any of the `OUTER JOIN`s, additional logic needs to be specified to handle `NULL`s in the result and constraints.

## the `OUTER` keyword

You might see queries with the outer joins written as `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, `FULL OUTER JOIN`. The `OUTER` keyword in these queries only exists for compatibility reasons. The queries are identical to there counterparts that don't specify the keyword:

- `LEFT OUTER JOIN` = `LEFT JOIN`
- `RIGHT OUTER JOIN` = `RIGHT JOIN`
- `FULL OUTER JOIN` = `FULL JOIN`