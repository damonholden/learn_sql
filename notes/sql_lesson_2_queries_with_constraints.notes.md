# SQL Lesson 2: Queries with constraints

Basic `SELECT` statements can be useful for quickly viewing tables, but when tables reach large amounts of rows, it is difficult to read through that information.

To filter what is returned from a `SELECT` statement, you need the `WHERE` clause. The `WHERE` clause is applied to each row of the table to determine whether or not it should be included in the returned data.

```SQL
SELECT column, another_column, …
FROM mytable
WHERE condition
```

More complex `WHERE` clauses can be constructed by joining numerous `AND` or `OR` logical keywords.

```SQL
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```

Below are some useful operators for numerical data:

- standard numerical operators: `=, !=, < <=, >, >=` (example: `col_name != 4`)
- number is within range of two values (inclusive): `BETWEEN … AND …` (example: `col_name BETWEEN 1.5 AND 10.5`)
- number is not within range of two values (inclusive): `NOT BETWEEN … AND …` (example: `col_name NOT BETWEEN 1 AND 10`)
- Number exists in a list: `IN(…)` (example: `	col_name IN (2, 4, 6)`)
- Number does not exist in a list: `NOT IN (…)` (example: `col_name NOT IN (1, 3, 5)`)

In addition to making query results easier to understand, writing `WHERE` clauses to constrain the set of rows returned also allows the query to run faster as the data being generated and returned is smaller.
