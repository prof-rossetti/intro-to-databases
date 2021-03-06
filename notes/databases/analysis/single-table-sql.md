# Single-table SQL

This document provides an overview of common SQL clauses, functions, and considerations for performing SQL analysis on a single database table.

## Clauses

### SELECT

The `SELECT` clause specifies the attributes to be included in the resulting dataset.

```` sql
SELECT "fun times"
````

```` sql
SELECT 2
````

```` sql
SELECT 2+2
````

Selecting multiple attributes into a single resulting dataset.

```` sql
SELECT
  "fun times",
  2,
  2 + 2
````

### FROM

The `FROM` clause is mandatory except for non-table-related selections and functions.
 It specifies the database table from which to select results.

```` sql
SELECT attribute_name
FROM table_name
````

```` sql
SELECT
  attribute_a
  ,attribute_b
FROM table_x
````

To select all attributes from a given table,
 use a star (`*`) to denote all attributes instead of listing each attribute by name.

```` sql
SELECT *
FROM table_x
````

> NOTE: `SELECT *` is slower than selecting each attribute by name.

### WHERE

The `WHERE` clause is optionally used to
 filter the set of returned results according to one or more logical conditions.

The queries below illustrate common logical operations, and how each may be used within the context of a where clause.

> TIP: Unlike attribute names, database names, and other reserved keywords recognized by the DBMS, attribute values of most datatypes (e.g strings, text, dates, etc.) are referenced by quotation marks.

```` sql
SELECT
 attribute_a
 ,attribute_b
FROM table_x
WHERE attribute_b = "some specific value" -- equal to
````

```` sql
SELECT
 attribute_a
 ,attribute_b
FROM table_x
WHERE attribute_b <> "some specific value" -- not equal to
````

```` sql
SELECT
 attribute_a
 ,attribute_b
FROM table_x
WHERE attribute_b > "some numeric value" -- greater than, less than, etc.
````

```` sql
SELECT
 attribute_a
 ,attribute_b
FROM table_x
WHERE attribute_b >= "some numeric value" -- greater than or equal to, less than or equal to, etc.
````

```` sql
-- open source dbms:
SELECT
  attribute_a
  ,attribute_b
FROM table_x
WHERE attribute_b LIKE "%some partial value%" -- string matching using `LIKE` operator and a wildcard string matcher

-- ms access dbms:
SELECT
  attribute_a
  ,attribute_b
FROM table_x
WHERE attribute_b LIKE "*some partial value*" -- string matching using `LIKE` operator and a wildcard string matcher
````

```` sql
SELECT
  attribute_a
  ,attribute_b
FROM table_x
WHERE attribute_b IN ("specific value 1", "specific value 2") -- inclusion in a list
````

```` sql
SELECT *
FROM my_table
WHERE attribute_a IS NULL -- lack of any value
````

```` sql
SELECT *
FROM my_table
WHERE attribute_a IS NOT NULL -- presence of any value
````

### ORDER BY

The `ORDER BY` clause is optionally used to
 specify the attributes and method for sorting the resulting data set.

```` sql
SELECT *
FROM my_table
ORDER BY attribute_a -- sort in ascending order (ASC) by default
````

```` sql
SELECT *
FROM my_table
ORDER BY attribute_a DESC -- sort in descending order
````

### LIMIT/TOP

The `LIMIT` clause is optionally used to restrict the total number of results returned. The limit clause, when used in a query, must be the final clause.

MS Access instead recognizes `TOP`, a [sub-clause of the select clause](http://www.w3schools.com/sql/sql_top.asp), for this purpose.

```` sql
-- open source dbms:
SELECT *
FROM table_a
LIMIT 200

-- ms access dbms:
SELECT
  TOP 200 *
FROM table_a
````

## Other Considerations

### Distinctness

Use `DISTINCT` as a sub-clause of the select clause to return only a set of unique records.

```` sql
SELECT DISTINCT attribute_a -- returns only unique values of attribute_a
FROM table_z
````

```` sql
SELECT
  DISTINCT
    attribute_a
    ,attribute_b
    ,attribute_c -- returns only unique value combinations of the set of all selected attributes
FROM table_z
````
