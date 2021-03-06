# sql-cheat-sheet
## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)  `MISCELLANEOUS`
1. CHAR_LENGTH function: Returns the length of character in a particular string
```sql
SELECT CHAR_LENGTH(product) 
FROM blank_details W
HERE product='paycard';
```

2. UPPER and LOWER: Used to change the case of any string
```sql
SELECT UPPER(product) FROM blank_details

// Gives the name of Products in Upper case
```

3. DATE
```sql
Entering the current date
INSERT INTO bank_holiday(holiday_date) VALUES(CURRENT_DATE())

Incrementing the date by some days
UPDATE bank_holiday
SET holiday = DATE_ADD(holiday, INTERVAL 3 DAY)
```

4. Using aggregate functionsMAX< COUNT, MIN, AVG, SUM: Use the nested query
Example: Query the name of the player with max runs
```sql
SELECT player_name FROM cricket_1
WHERE runs = ( SELECT MAX(runs) FROM cricket_1)
```
5. Select all the columns from player table for the player with second highest runs
```sql
SELECT * FROM cricket_1
WHERE runs = (
    SELECT MAX(runs) as MAX_RUN_SECOND FROM cricket_1
	  WHERE runs <> (SELECT MAX(runs) FROM cricket_1)
)

SAME QURY CAN BE DONE BY ORDERBY DESC WITH LIMIT X OFFSET Y ( Given only X rows after first Y rows)
SELECT * FROM cricket_1
ORDER BY runs DESC LIMIT 1 OFFSET 1;
```

6. ANY and ALL
```
The ANY operator:

returns a boolean value as a result
returns TRUE if ANY of the subquery values meet the condition
ANY means that the condition will be true if the operation is true for any of the values in the range.

The ALL operator:

returns a boolean value as a result
returns TRUE if ALL of the subquery values meet the condition
is used with SELECT, WHERE and HAVING statements
ALL means that the condition will be true only if the operation is true for all values in the range. 
```
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

We use Aggregate functions in select while using group by as group by makes group and we cant return select value from a group: 
For Example: If we have grouped students table by Class then it is more meaningful to find the AVG(age) and not the age, as each group will be having lot of students and when you ask just the age then it is nonsense as it is not clear to give which student's age we asking?
```
Not meaning full, as here we get the first result of each group i.e age of just the first student
SELECT age FROM std GROUP BY age

Meaningful Query:
SELECT AVG(age) FROM std GROUP BY age
```
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

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `Order of Execution`

![image](https://user-images.githubusercontent.com/63506466/151922014-903ada50-4e80-4563-99d1-208a81a60459.png)

![image](https://user-images.githubusercontent.com/63506466/152645794-71289e46-6f1b-4e66-85c1-c560ba1a9df8.png)


**EXAMPLE**

![image](https://user-images.githubusercontent.com/63506466/151922117-b2fad5ce-0fa6-48a9-ac1f-d0cf15220f5b.png)

Query:

```sql
SELECT id, name FROM instructor WHERE salary>40000
GROUP BY id,name HAVING count(DISTINCT university) > 1
```
```
1. Here, first that id and name is selected whose salary is greater than 40K
2. From the filtered result, the grouping is then done using id and name. Here same id ans name pair are grouped together
3. From this group, we then filter that group(not row) which has the distinct university count greater than 1.
4. Groups after this filtering is returned. The first row of the selected groups are returned
```

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

## ![#f04c65](https://via.placeholder.com/15/f03c15/000000?text=+)  `JOINS`

1. INNER JOIN: The INNER JOIN keyword selects records that have matching values in both tables.
```sql
SELECT table1.column1, table2.column2...
FROM table1
INNER JOIN table2
ON table1.common_field = table2.common_field;

EXAMPLE:
SELECT users.email, passwords.name FROM users
INNER JOIN passwords
ON users.email = passwords.email
```
Password: 

![image](https://user-images.githubusercontent.com/63506466/151703898-11cbffaa-a62e-48c5-a824-72f49fa904e3.png)

Users: 

![image](https://user-images.githubusercontent.com/63506466/149613585-1d13a8f4-1fb9-4f00-96ac-66318f157f30.png)

Output: 

![image](https://user-images.githubusercontent.com/63506466/149613560-ecc7840c-66af-444f-8e5b-579b9ef03809.png)

2. NATURAL JOIN: The NATURAL JOIN is nothing but the rows with same values for the common attributes. After doing cross product of two tables we see which rows have the same values for common attributes on both the tables
```sql
SELECT productName from t1 NATURAL JOIN t2
```
3. LEFT JOIN: The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;

EXAMPLE:
SELECT * 
FROM users
LEFT JOIN passwords
ON users.email = passwords.email

HERE, USERS IS LEFT TABLE AND PASSWORDS IS RIGHT TABLE. 
HERE FOR EACH EMAIL OF LEFT TABLE(USERS) IT FINDS SAME EMAIL IN RIGHT TABLE(PASSWORDS).
ALL THE MATCHING IS RETURNED.
EXAMPLE: FOR `iit2016107@iiita.ac.in` WE HAVE MORE THAN ONE MATCHING IN PASSWORD, THEN BOTH THE MATCHINGS ARE RETUNED.SEE IMAGE
IF NOT MATCHING IS FOUND WE SEE NULL 
```
![image](https://user-images.githubusercontent.com/63506466/151703694-a281a55b-576c-4f8c-ac10-b49d411a3f95.png)


4. RIGHT JOIN:The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;

SELECT * 
FROM users
RIGHT JOIN passwords
ON users.email = passwords.email

LEFT TABLE IS USERS AND RIGHT TABLE IN PASSWORDS
ALL THE EMAILS OF RIGHT TABLE PASSWORDS IS MATHCED WITH LEFT TABLE USERS.
FOR EACH MATCHING IN LEFT RECORD IS RETURNED. MULTIPLE ROWS MIGHT MATCH AND ALL OF THEM ARE RETURNED
IF NOT MATHCING IS FOUND FOR ANY RIGHT EMAIL THEN NULL VALUE IS RETURNED
```
![image](https://user-images.githubusercontent.com/63506466/151703872-a0238056-a153-461c-aae4-3402d27bbc48.png)




5. SELF JOIN: A self join is a regular join, but the table is joined with itself.
The following SQL statement matches customers that are from the same city:
```sql
SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID
AND A.City = B.City
ORDER BY A.City;
```
