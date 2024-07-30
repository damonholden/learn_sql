# SQL Lesson 1: SELECT queries 101

To retrieve data from a SQL database, you need to write `SELECT` statements. `SELECT` statements are often referred to as queries. A query is just a statement which declares the data to find, where to find it in the database, and optionally, how to transform it before it is returned.

Given a table of dogs, where each row is a type of dog (pug, beagle, labrador, etc.) and each column represents the shared properties of each type of dog (average height, tail length, fur color, etc.), the most basic query would be one that grabs a column from every row:

```SQL
SELECT "fur color"
FROM mytable;
```
The result of this query would effectively be a copy of the table with only one column - `fur color`. A query like this is a good way to view a table with only the columns that are of interest.

To get what is effectively a copy of the entire table - the asterisk (`*`) shorthand can be used following the SELECT statement to get every column from the table, as opposed to naming all the column names individually:

```SQL
SELECT "fur color"
FROM mytable;
```

## table structure to entity terminology

It's worth noting the Table structure to entity terminology key:

- Table: entity
- row: instance
- column: property
