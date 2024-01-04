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

