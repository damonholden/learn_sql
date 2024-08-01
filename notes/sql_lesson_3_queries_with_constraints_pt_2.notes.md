# SQL Lesson 3: Queries with constraints (Pt. 2)

When writing `WHERE` clauses with columns containing text data, SQL supports some useful operators:

- Case sensitive exact string comparison: `=` (`col_name = "abc"`)
- Case sensitive exact string inequality comparison: `!=`/`<>` (`col_name != "abcd"`)
- Case insensitive exact string comparison: `LIKE` (`col_name LIKE "ABC"`)
- Case insensitive exact string inequality comparison: `NOT LIKE` (`col_name NOT LIKE "ABCD"`)
- Match any sequence of zero or more characters (only works with `LIKE` or `NOT LIKE`): `%` (`col_name LIKE "%AT%"` - matches `"AT"`, `"ATTIC"`, `"CAT"` or even `"BATS"`)
- Match any single character (only works with `LIKE` or `NOT LIKE`): `-` (`col_name LIKE "AN_"` - matches `"AND"`, but not `"AN"`)
- String exists in a list: `IN (…)` (`col_name IN ("A", "B", "C")`)
- String does not exist in a list: `NOT IN (…)` (`col_name NOT IN ("D", "E", "F")`)

While most database implementations are efficient at using these operators, full-text search is best left to dedicated libraries like Apache Lucene or Sphinx. These Libraries are designed specifically to do full-text search, and a a result are more efficient anc can support a wider variety of search features.
