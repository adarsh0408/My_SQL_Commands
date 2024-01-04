# MySQL Commands Cheat Sheet - Database Operations

# Table of Contents

1. [Database Operations](#1-database-operations)
2. [User Management](#2-user-management)
2. [Table Operations](#3-table-operations)
3. [Constraints](#constraints)
4. [Keys in SQL](#keys-in-sql)
5. [Joins in SQL](#joins-in-sql)

## 1. Database Operations

### Create a new database

Creates a new database with the specified name.
```sql
CREATE DATABASE database_name;
```
### Show all databases

```sql
SHOW DATABASES;
```

### Switch to a database

```
USE database_name;
```
### Delete a database

```
DROP DATABASE database_name;
```

## 2. User Management

### Create a new user

```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```
Creates a new MySQL user with a specified username and password.

### Grant privileges to a user

```
GRANT privilege(s) ON database_name.table_name TO 'username'@'localhost';
```
Grants specific privileges to a user on a specified database or table.

### Revoke privileges from a user

```
REVOKE privilege(s) ON database_name.table_name FROM 'username'@'localhost';
```

Revokes specific privileges from a user on a specified database or table.

### Change user password

```
SET PASSWORD FOR 'username'@'localhost' = 'new_password';
```

## 3. Table Operations

### Create a new table
```sql
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  ...
);
```
### Show table structure

```
DESCRIBE table_name;
```

### Rename a table

```
RENAME TABLE old_table_name TO new_table_name;
```

### Delete a table

```
DROP TABLE table_name;
```

### Alter table - Add a new column

```
ALTER TABLE table_name ADD column_name datatype;
```

### Alter table - Modify a column

```
ALTER TABLE table_name MODIFY column_name new_datatype;
```

### Alter table - Rename a column

```
ALTER TABLE table_name CHANGE old_column_name new_column_name datatype;
```

### Alter table - Drop a column

```
ALTER TABLE table_name DROP column_name;
```

### Truncate a table

```
TRUNCATE TABLE table_name;
```

### Copy data from one table to another

```
INSERT INTO new_table_name SELECT * FROM old_table_name;
```

### Backup a table

```
CREATE TABLE backup_table_name AS SELECT * FROM original_table_name;
```

### Show indexes on a table

```
SHOW INDEX FROM table_name;
```

### Add an index to a table

```
CREATE INDEX index_name ON table_name (column1, column2, ...);
```

### Remove an index from a table

```
DROP INDEX index_name ON table_name;
```

### Enable or disable keys for a table

```
ALTER TABLE table_name DISABLE KEYS;
ALTER TABLE table_name ENABLE KEYS;
```

### Show table size
```
SHOW TABLE STATUS LIKE 'table_name';
```

###  Repair a table

```
REPAIR TABLE table_name;
```
Repairs a corrupted table.

### Optimize a table

```
OPTIMIZE TABLE table_name;
```

Optimizes the storage of a table, defragmenting the data file and reclaiming unused space.

### Change storage engine for a table
```
ALTER TABLE table_name ENGINE = new_engine;
```

## 4. Data Manipulation

### Insert data into a table
```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);
```

### Update data in a table
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```

### Delete data from a table
```sql
DELETE FROM table_name WHERE condition;
```

### Query data from a table

```sql
SELECT column1, column2, ... FROM table_name WHERE condition;
```

### SELECT DISTINCT values

```sql
SELECT DISTINCT column_name FROM table_name;
```

### ORDER BY
Order by a single column
```sql
SELECT * FROM table_name ORDER BY column_name;

SELECT * FROM table_name ORDER BY column_name DESC;
```

Order by multiple columns
```sql
SELECT * FROM table_name ORDER BY column1, column2 DESC;
```

### GROUP BY

Group by a single column
```sql
SELECT column, COUNT(*) FROM table_name GROUP BY column;
```
Group by multiple columns

```sql
SELECT column1, column2, COUNT(*) FROM table_name GROUP BY column1, column2;
```

### LIMIT
Retrieve a limited number of rows
```sql
SELECT * FROM table_name LIMIT 10;
```
Retrieve rows with an offset
```sql
SELECT * FROM table_name LIMIT 10 OFFSET 5;
```

### Aggregate Functions

Count rows
```sql
SELECT COUNT(*) FROM table_name;
```
Sum values
```sql
SELECT SUM(column_name) FROM table_name;
```
Average value
```sql
SELECT AVG(column_name) FROM table_name;
```
Minimum value
```sql
SELECT MIN(column_name) FROM table_name;
```
Maximum value
```sql
SELECT MAX(column_name) FROM table_name;
```

### String Functions

Concatenate strings
```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM table_name;
```
Substring
```sql
SELECT SUBSTRING(column_name, start_position, length) FROM table_name;
```
Upper and Lowercase
```sql
SELECT UPPER(column_name) FROM table_name;
SELECT LOWER(column_name) FROM table_name;
```
### NULL Handling
Filter NULL values
```sql
SELECT * FROM table_name WHERE column_name IS NOT NULL;
```

Coalesce NULL values
```sql
SELECT COALESCE(column_name, 'Default') FROM table_name;
```

## Joins

### INNER JOIN
The INNER JOIN keyword selects records that have matching values in both tables.
```sql
SELECT * FROM table1 INNER JOIN table2 ON table1.column = table2.column;
```

### LEFT JOIN (or LEFT OUTER JOIN)

Retrieves all rows from the left table and matching rows from the right table.
```sql
SELECT * FROM table1 LEFT JOIN table2 ON table1.column = table2.column;
```
### RIGHT JOIN (or RIGHT OUTER JOIN)

Retrieves all rows from the right table and matching rows from the left table.
```sql
SELECT * FROM table1 RIGHT JOIN table2 ON table1.column = table2.column;
```
### FULL JOIN (or FULL OUTER JOIN)
Retrieves all rows when there is a match in either table.
```sql
SELECT * FROM table1 FULL JOIN table2 ON table1.column = table2.column;
```
### CROSS JOIN
Produces the Cartesian product of two tables.
```sql
SELECT * FROM table1 CROSS JOIN table2;
```

## Keys and Indexes

### Primary Key
```sql
CREATE TABLE table_name (
  id INT PRIMARY KEY,
  column1 datatype,
  column2 datatype,
  ...
);
```
### Composite Primary Key
```sql
CREATE TABLE table_name (
  id1 INT,
  id2 INT,
  PRIMARY KEY (id1, id2)
);
```

### Foreign Key

```sql
CREATE TABLE table_name1 (
  id INT PRIMARY KEY,
  column1 datatype,
  column2 datatype,
  ...
);

CREATE TABLE table_name2 (
  id INT PRIMARY KEY,
  table1_id INT,
  FOREIGN KEY (table1_id) REFERENCES table_name1(id)
);
```

### Unique Key

```sql
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  UNIQUE (column1)
);
```
### Index

```sql
CREATE INDEX index_name ON table_name (column1, column2, ...);
```

### Full-Text Index

```sql
CREATE FULLTEXT INDEX index_name ON table_name (column1, column2, ...);
```

### Show Indexes on a Table

```sql
SHOW INDEX FROM table_name;
```

### Add a Primary Key to existing table

```sql
ALTER TABLE table_name ADD PRIMARY KEY (column1);
```

### Add a Unique Constraint to existing table
```sql
ALTER TABLE table_name ADD UNIQUE (column1);
```

### Add an Index to existing table

```sql
ALTER TABLE table_name ADD INDEX index_name (column1, column2, ...);
```

### Add a Full-Text Index to existing table

```sql
ALTER TABLE table_name ADD FULLTEXT INDEX index_name (column1, column2, ...);
```

### Drop a Primary Key
```sql
ALTER TABLE table_name DROP PRIMARY KEY;
```

### Drop a Unique Constraint

```sql
ALTER TABLE table_name DROP INDEX index_name;
```

### Drop an Index
```sql
ALTER TABLE table_name DROP INDEX index_name;
```

### Drop a Full-Text Index

```sql
ALTER TABLE table_name DROP INDEX index_name;
```
