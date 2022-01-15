# sql-cheat-sheet
## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `ALTER TABLE (DDL)`

### ALTER TABLE - ADD Column
```sql
ALTER TABLE table_name
ADD column_name datatype;
```
### ALTER TABLE - DROP COLUMN
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

### ALTER TABLE - ALTER/MODIFY COLUMN
```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `UPDATE (DML)`
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. 
The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, 
all records in the table will be updated!

## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `INSERT INOT (DML)`
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `DELETE FROM (DML)`
```sql
DELETE FROM table_name WHERE condition;
```

## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `SELECT DISTINCT`
The SELECT DISTINCT statement is used to return only distinct (different) values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `OPERATORS IN SQL`
AND, OR, and NOT operators
The AND and OR operators are used to filter records based on more than one condition:

* The AND operator displays a record if all the conditions separated by AND are TRUE.
* The OR operator displays a record if any of the conditions separated by OR is TRUE.
* The NOT operator displays a record if the condition(s) is NOT TRUE.

AND:
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```
AND:
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```
NOT:
```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `BETWEEN`
```sql
SELECT name FROM t2
WHERE age BETWEEN 20 AND 39 AND name ="Prashant"
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `AGGREGATE FUNCTIONS`

1. MAX: The MAX() function returns the largest value of the selected column.
2. MIN: The MIN() function returns the smallest value of the selected column.
```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;

SELECT MIN(column_name)
FROM table_name
WHERE condition;
```
3. COUNT: The COUNT() function returns the number of rows that matches a specified criterion.
4. AVG: The AVG() function returns the average value of a numeric column. 
5. SUM: The SUM() function returns the total sum of a numeric column. 
```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

SELECT AVG(column_name)
FROM table_name
WHERE condition;

SELECT SUM(column_name)
FROM table_name
WHERE condition;
```


## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `LIKE Operator`
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

* The percent sign (%) represents zero, one, or multiple characters
* The underscore sign (_) represents one, single character
<img src ="https://user-images.githubusercontent.com/63506466/149466976-b347fe90-fd5d-4957-97a0-66249b6d3172.png" width="700">

EG: Select the name which starts with 'Pr" and ends with 'ant' ans has atleast one character between them
```sql
SELECT name FROM t2 
WHERE name LIKE "Pr_%ant";
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `LIMIT`
The LIMIT clause is used to specify the number of records to return.
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `ORDER BY`
The ORDER BY keyword is used to sort the result-set in ascending or descending order.

The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
Syntax:
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

EXAMPLE: The following SQL statement selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName:
```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `GROUP BY`
The GROUP BY Statement in SQL is used to arrange identical data into groups with the help of some functions. i.e if a particular column has same values in different rows then it will arrange these rows in a group.
* GROUP BY clause is used with the SELECT statement.
* In the query, GROUP BY clause is placed after the WHERE clause.
* In the query, GROUP BY clause is placed before ORDER BY clause if used any.
* GROUP BY returns only one result per group of data.

Example:
```sql
SELECT class, COUNT(name) FROM t2
GROUP BY class
```
![image](https://user-images.githubusercontent.com/63506466/149610262-6e218c00-f8c6-4be0-ba1a-00573edf69ae.png)

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `HAVING Clause`
HAVING Clause utilized in SQL as a conditional Clause with GROUP BY Clause. This conditional clause returns rows where aggregate function results matched with given conditions only. It added in the SQL because WHERE Clause cannot be combined with aggregate results, so it has a different purpose. The primary purpose of the WHERE Clause is to deal with non-aggregated or individual records.

HAVING Clause always utilized in combination with GROUP BY Clause.
HAVING Clause restricts the data on the group records rather than individual records.
WHERE and HAVING can be used in a single query.

```sql
SELECT class, COUNT(name) FROM t2
GROUP BY class
HAVING COUNT(name) < 9
```
![image](https://user-images.githubusercontent.com/63506466/149610380-9d89da05-d899-4eb8-b8c9-e04106c8a5bc.png)


## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `UNION`
The UNION operator is used to combine the result-set of two or more SELECT statements.

* Every SELECT statement within UNION must have the same number of columns
* The columns must also have similar data types
* The columns in every SELECT statement must also be in the same order
* The UNION operator selects only distinct values by default. To allow duplicate values, use UNION ALL:
```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `NULL`
It is not possible to test for NULL values with comparison operators, such as =, <, or <>.

We will have to use the IS NULL and IS NOT NULL operators instead.
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `IN`
* The IN operator allows you to specify multiple values in a WHERE clause.
* The IN operator is a shorthand for multiple OR conditions.

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);

OR


SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);

EXAMPLE:
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

EXAMPLE:
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);

```
