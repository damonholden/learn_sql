# SQL Lesson 4: Filtering and sorting query results

Even though rows in a SQL table will all be unique, that doesn't mean the results of a query will be. When selecting all the rows out of a table by a single non-unique column, for example, the results may provide duplicate values, which might not be desirable. SQL provides a keyword to discard duplicate rows from results -`DISTINCT`.

The syntax for using the `DISTINCT` keyword looks like the following:

```SQL
SELECT DISTINCT column, another_column, ...
FROM mytable
WHERE condition(s);
```

## Ordering results

Most data in real databases are added in no particular order, so it can be tricky to read through the query results of large unordered tables. To help with this, SQL provides a way to sort results by a given column in ascending or descending order using the `ORDER BY` clause.

```SQL
SELECT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

When an `ORDER BY` clause is used, each row is sorted alpha-numerically based on the columns value. Some databases even support specifying a collation to better sor data containing international text.

## Limiting results to a subset

Clauses which are used commonly with the `ORDER BY` clause are the `LIMIT` and `OFFSET` clauses:

- The `LIMIT` clause will will reduce the number of rows to return.
- The optional `OFFSET` clause will specify where to begin counting the rows from.

```SQL
SELECT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

Using `ORDER BY` with `LIMIT` and/or `OFFSET` can be practically imagined with websites like reddit, where posts are **ordered** by popularity, and different pages on a subreddit correspond to different **limited offsets** in a database table.
