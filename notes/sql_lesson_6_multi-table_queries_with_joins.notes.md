# SQL lesson 6: multi-table queries with `JOIN`s

While conceptually its easy to think of rows in a single table (like a table of dog breeds), often in real-world databases, data is broken down into pieces and stored across multiple tables using a process known as normalisation.

## Database Normalisation

Database normalisation is useful because it minimizes duplicate data in tables and allows data to grow independently of each other.

For example, if a `cars` database table has an `engine name` column and an `engine size` column, the `engine size` column's value for any given row should always depend on the value of `engine name`. It may make sense in this case to move the engine information to a separate table and link it to the `cars` table with maybe an `engine id` column.

The trade-off with database normalization is that it makes queries more complex since they now need to generate data from multiple tables. Additionally, performance issues may arise when pulling data from many large tables.

## Multi-table queries with JOINs

Tables that have entities referenced in another table need to have a primary key that identifies that entity uniquely within the table. One common primary key type is an auto-incrementing integer (because they are space efficient), but it can be any value, as long as its unique.

Using the `JOIN` clause in a query, rows of data can be combined across separate tables using a unique key. One such `JOIN` clause is the `INNER JOIN`:

```SQL
SELECT column, another_table_column, ...
FROM mytable
INNER JOIN another_table
	ON mytable.id = another_table.id
```

`INNER JOIN` matches rows from two tables that have the same key (as defined by `ON` constraint) to create a result with the combined columns from both tables. The results of an `INNER JOIN` can be manipulated with other clauses like `WHERE`, `ORDER BY`, and `LIMIT` just like normal queries:

```SQL
SELECT column, another_column, ...
FROM myTable
INNER JOIN anotherTable
	ON myTable.id = anotherTable.id
WHERE condition(s)
ORDER BY column, ... ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## `INNER JOIN` vs `JOIN`

`INNER JOIN` and `JOIN` have the same effect but `INNER JOIN` is preferred if readability is important as it makes more sense in the context of the other `JOIN` clauses.
