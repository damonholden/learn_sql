# SQL Lesson 9: Queries with expressions

SQL "expressions" can be used to write more complex logic on column values in a query. These expressions can use mathematical and string functions along with basic arithmetic to transform values when the query is executed:

```SQL
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```

Each database has its own supported set of mathematical, string, and date functions that can be used in a query, which can be found in the database's respective docs.

While using sql expressions can save time and extra post-processing of the result data, they can make the query harder to read, so when using expressions in the `SELECT` part of the query, that the expressions are given a descriptive alias using the `AS` keyword:

```SQL
SELECT col_expression AS expr_description, ...
FROM mytable;
```

In addition to expressions - regular columns and even tables can also have aliases to make them easier to reference in the output and to make complex queries easier to read:

```SQL
SELECT column AS better_column_name, ...
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN widget_sales
	ON mywidgets.id = widget_sales.widget_id;
```