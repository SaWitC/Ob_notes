#questions
### 1. <span style="color:#fdd052"> Base base sql statements such</span> 
- Select (The `SELECT` statement is used to select data from a database.)
```sql
Select * from tableName
```
- Where (The `WHERE` clause is used to filter records.)
```sql
Select * from tableName where status = 'active'
```
- Joins (A `JOIN` clause is used to combine rows from two or more tables, based on a related column between them.)
- Order By (The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.)
```sql
Select * from tableName order by status
```
- Group BY 
(The `GROUP BY` statement groups rows that have the same values into summary rows, like "find the number of customers in each country".

The `GROUP BY` statement is often used with aggregate functions (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to group the result-set by one or more columns.)
```sql
Select * from tableName group by status
```
- Having (The `HAVING` clause was added to SQL because the `WHERE` keyword cannot be used with aggregate functions)
```sql
SELECT _column_name(s)_  
FROM _table_name_  
WHERE _condition_  
GROUP BY _column_name(s)  
HAVING _condition  
ORDER BY _column_name(s);_
```
### 2. <span style="color:#fdd052">Create/Drop/Backup Database</span>
1. Create Database  (is a command that used to create database)
``` sql
CREATE DATABASE _databasename_;
```
2. Drop Database  (is a command that used to create database)
```sql
DROP DATABASE _databasename_;
```
3. BACKUP DATABASE (The `BACKUP DATABASE` statement is used in SQL Server to create a full back up of an existing SQL database.)
```sql
BACKUP DATABASE _databasename_  
TO DISK = '_filepath_';
``` 
### 3. <span style="color:#fdd052">Create/Drop/Alert Table</span> 
1. CREATE TABLE (The `CREATE TABLE` statement is used to create a new table in a database.)
```sql
CREATE TABLE Persons (  
    PersonID int,  
    LastName varchar(255),  
    FirstName varchar(255),  
    Address varchar(255),  
    City varchar(255)  
);
```
2. DROP TABLE (The `DROP TABLE` statement is used to drop an existing table in a database.)
```sql
DROP TABLE _table_name_;
```
3. ALTER TABLE (The `ALTER TABLE` statement is used to add, delete, or modify columns in an existing table.)
``` sql
ALTER TABLE Customers  
ADD Email varchar(255);

--OR

ALTER TABLE Customers  
DROP COLUMN Email;
```
### 4. <span style="color:#fdd052">indexes </span> 
- Clustered( main index,
- non clustered 
- partial index (applies only to some data matching its filter) example of an index that applies only to non-deleted data
### 6. <span style="color:#fdd052">how to select unique data using select operator </span> 
### 7. <span style="color:#fdd052">what operators you can use with where </span> 
- <> > < = >=<=
- and or not
- is null is not null
- between
- in
- Like
### 8. <span style="color:#fdd052">what is the difference betwen where and join </span> 
### 10. what is the difference betwene join and inner join (it is the same)
### 11. What for we use Alert table (to modify table add or remove fields)
### 12. how to create table using exsisting one (create table new_Table as select * from exsisting table)
### 13. what is the difference betwen drop  table and truncate table ( drop remove table, truncate remove element)
### 14. what for we use keys in sql
we use keys to identify data in the table

### 15 what kind of keys exsist
unique key
foreign key
primary key
