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
