## Built-in Functions

> NOTE: this document is in DRAFT status for now. It needs updating.

Consult DBMS-specific documentation for a comprehensive list of functions and instructions on how to use them.

```` sql
SELECT
-- mysql dbms:
  cast('2016-11-06' AS DATETIME) AS scheduled_at
  ,cast('2016-11-06' AS DATE) AS scheduled_on
````

### String Functions

```` sql
-- mysql dbms:
SELECT concat('Hello', ' ', 'world') AS my_message
````

### Date Functions

```` sql
-- mysql dbms:
SELECT
  now() AS datetime_right_now
  ,curdate() AS date_right_now
  ,curtime() AS time_right_now
  ,date_format(curdate(), '%b') AS this_month_abbrev
  ,date_format(curdate(), '%Y-%b') AS this_year_and_month
````

### Conditional Functions

```` sql
-- mysql dbms:
SELECT
  courses.registration_name
  ,IF(courses.registration_name LIKE "%ISTM%", "Information Systems Department", "Other Department") AS department_classification
  ,CASE
      WHEN courses.registration_name LIKE '%ISTM%' THEN 'Information Systems Department'
      WHEN courses.registration_name LIKE '%BADM%' THEN 'Business Administration Department'
      WHEN courses.registration_name LIKE '%MKTG%' THEN 'Marketing Department'
      ELSE 'Other Department'
  END department_name
FROM (
  SELECT "MKTG-1414-10" AS registration_name -- change this value and see what happens ...
) courses
````

```` sql
-- mysql dbms:
SELECT
  NULL -- evaluates to NULL
  ,coalesce(NULL,0) -- evaluates to 0
````
