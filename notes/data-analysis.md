# Structured Query Language (SQL)

SQL is the language of relational databases.
 All major RDBMS tools recognize SQL.

SQL enables a human to ask questions of the database management system in an automated, programmatic way.

SQL helps humans transform **data** into **information**.

## Clauses

Like an English sentence, each SQL query is comprised of one or more clauses.

Here are all the clauses available for use in a SQL query, in the order they are to be used:

```` sql
SELECT ...
FROM ...
JOIN ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...
````

It is not necessary to use all clauses in a single query.

There is also a `UNION` clause used in special cases, but it is outside the scope of this course.

Additional clauses and sub-clauses exist, but may or may not be uniformly recognized across DBMSs. For example, open source DBMS like MySQL and PostgreSQL recognize a stand-alone `LIMIT` clause, whereas MS Access instead recognizes `TOP` as a sub-clause of the select clause. Beware of DBMS differences, and use your knowledge to inform your DBMS preferences.
