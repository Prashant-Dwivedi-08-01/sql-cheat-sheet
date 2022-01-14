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
