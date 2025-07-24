# SQL Basics – Notes 1

## What is SQL?
SQL (Structured Query Language) is used to retrieve and manage data from relational databases using CRUD operations.  
CRUD = **Create**, **Read**, **Update**, and **Delete**

## Common SQL Commands:
- `SELECT`: to read data
- `UPDATE`: to update data
- `DELETE`: to delete data
- `WHERE`: to filter specific rows
- `LIMIT`: to restrict the number of rows returned

## Example Query:
```sql
SELECT name, age
FROM employees
WHERE department = 'Engineering'
LIMIT 10;