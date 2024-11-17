# SQL Lesson 12: Order of execution of a query

having learned all the parts of a query, its important to understand how they all fit together in the context of a complete query:

```SQL
SELECT DISTINCT column, AGG_FUNC(column_or_expression), .
FROM mytable
	JOIN another_table
		ON mytable.column = another_table.column
	WHERE constraint_expression
	GROUP BY column
	HAVING constraint_expression
	ORDER BY column ASC/DESC
	LIMIT count OFFSET COUNT;
```

Every SQL query begins with finding the data needed in the database and then filters the data down. Because each part of the query is executed sequentially, its important to understand the order of execution so that you know what data is accessible at any given point of a query when nmaking mmodifications.

## Query order of execution

1. `FROM` and `JOIN`s

The `FROM` clause and susequent `JOIN` clauses are the first to be executed to determine the total working set of data being queried. This includes subqueries in either of these clauses. These clauses may also generate temporary tables that contain all the rows and columns resulting from the join.

2. `WHERE`

Once the working set of data has been generated, each `WHERE` clause is processed in order and at each `WHERE` clause execution any rows that do not satisy the constraint are discarded for further steps. Aliases in the `SELECT` part of the query are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.

3. `GROUP BY`

The resulting rows from the `WHERE` constraints are grouped based on common values in the column specified by the `GROUP BY` clause. The resulting table will only have as many rows as unique values in the specified column. Implicitly, this means that you should have aggregate functions in the query, as there is no reason to group rows otherwise.

4. `HAVING`

If the query has a `GROUP BY` clause, then the constraints in the `HAVING` clause are then applied to the grouped rows. Grouped rows that do not satisfy the constraint are discarded. Similar to the `WHERE` clause, aliases are also not accessible from this step in most databases.

5. `SELECT`

Any expressions in the SELECT part of the query are compluted.

6. `DISTINCT`

Of the remaining rows, rows with duplicate values in the column marked as `DISTINCT` will be discarded.

7. `ORDER BY`

if an order is specified by the `ORDER BY` clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the `SELECT` part of the query have been computed by this point, you can reference aliases in this clause.

8. `LIMIT` / `OFFSET`

Finally, the rows that fall outside the range specified by `LIMIT` and `OFFSET` are discarded, leaving the final set of rows to be returned from the query.

## Conclusion

Utilising these queries effectively allows us to query and minipulate data in complex ways without having to change the fundamental data.