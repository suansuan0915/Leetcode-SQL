# SQL

NOT case sensitive.\
\
Some database systems require a semicolon at the end of each SQL statement.

- Field:\
a column in the table.

- Record:\
also called a row, is each individual entry that exists in a table.\
\
A database most often contains one or more tables. Each table is identified by a name (e.g. "Customers" or "Orders"). Tables contain records (rows) with data.

## important SQL commands
![image](https://user-images.githubusercontent.com/51430523/138033681-a1730298-d1fc-4f86-9a3c-518208560187.png)

- Primary Key vs. Foreign Key\
  The table w/ primary key is *parent table* or *reference table*.\
  The table with the foreign key is called *child table*.\
  Foreign key is created only when primary key in parent table has been created.\
  Like: Persons table (PersonId -> primary key), Orders table (PersonId -> foreign key).\
  --> Sometimes, it's safer to use `LEFT JOIN` on parent table to kid table (instead of `INNER JOIN`), because not all primary key values exist in kid table.

- `SELECT DISTINCT`\
  return only distinct (different) values.\
  ![image](https://user-images.githubusercontent.com/51430523/138033814-d109271b-e8c1-4f59-b976-6c1c582dd4de.png)

- Operators in `WHERE`\
  **`WHERE` cannot be used with aggregate functions!**
  ![image](https://user-images.githubusercontent.com/51430523/138034050-a00a1068-c885-4763-9a91-05b53f53460c.png)

- `ORDER BY`\
  sort the result-set in ascending or descending order.\
  ![image](https://user-images.githubusercontent.com/51430523/138034256-f2ced13f-dfd7-4911-87c5-61f3a2e455da.png)

- `INSERT INTO`\
  insert new records in a table.\
  ![image](https://user-images.githubusercontent.com/51430523/138034431-17a773e8-cd7b-4eea-9f63-e67a4ace43cb.png)\
  no specified record will have "null" value.

- Difference of `TRUNCATE TABLE` and `DROP TABLE`\
  DROP: delete the table and all data in it.\
  TRUNCATE: empty all data from the table but keep the table itself.

- null:\
  A NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record creation!\
  can use "=" to check null, use `IS NULL` `IS NOT NULL`.
  
- `UPDATE`\
  modify the existing records in a table.\
  ![image](https://user-images.githubusercontent.com/51430523/138035829-2f7261dd-ec62-427a-9fb6-021704eca5b8.png)
  ![image](https://user-images.githubusercontent.com/51430523/138035993-e19c5b32-9a88-4eae-b2c0-1c0365953db0.png)

- `DELETE`\
  ![image](https://user-images.githubusercontent.com/51430523/138036144-14470937-9a8b-42b5-ac89-818849dfb9cc.png)\
  The following SQL statement deletes all rows in the "Customers" table, without deleting the table:\
  ![image](https://user-images.githubusercontent.com/51430523/138036260-697288a5-0da6-491f-b6db-ab0d736810f5.png)

- `SELECT TOP` / `LIMIT` / `FETCH FIRST`\
  specify the number of records to return.\
  useful on large tables with thousands of records. Returning a large number of records can impact performance.
  
  - Not all database systems support the SELECT TOP clause:\
  SQL Server / MS Access Syntax: `SELECT TOP`\
  MySQL / PostgreSQL: `LIMIT`\
  oracle: `FETCH FIRST n ROWS ONLY`  and  `ROWNUM`\
  ![image](https://user-images.githubusercontent.com/51430523/138037164-f4af0cb9-1f6b-46b8-a566-d0cfcf0e3b34.png)
  ![image](https://user-images.githubusercontent.com/51430523/138037211-425dbb59-99fb-4717-989c-a55815060fec.png)

- `OFFSET`\
  `LIMIT ... OFFSET ...`\
  ![image](https://user-images.githubusercontent.com/51430523/138578187-7c43e42e-10b4-45da-8a73-b107ed3f5c53.png)\
  \
  OFFSET  clause skips the offset rows before beginning to return the rows. BUT it's optional.\
  OFFSET  skips offset rows first before the LIMIT  constrains the number of rows.

- `MIN()`  /  `MAX()`
  
- 区分`COUNT()` 和 `SUM()`
  
- 慎用 `AVG()`
  
- `LIKE`\
  ![image](https://user-images.githubusercontent.com/51430523/138218562-7a189a06-4b9e-4ab4-8c6e-50e50a86062d.png)
  ![image](https://user-images.githubusercontent.com/51430523/138218607-6f50431c-a9a1-4904-97f8-1f8c0590c733.png)\
  \
  two wildcards often used in conjunction with the LIKE operator:\
  ![image](https://user-images.githubusercontent.com/51430523/138218778-0365a1f0-d916-4c2c-8b37-dca617a437c9.png)

- Wildcards 通配符\
  in MySQL:\
  <img width="716" alt="image" src="https://github.com/suansuan0915/Leetcode-SQL/assets/51430523/18a97979-a687-4ae0-bbeb-af45a88ba745">\
  `ESCAPE`:\
  escape a wildcard character, like `SELECT ... LIKE '67#%%' ESCAPE '#'`, which means to find a pattern like '67%'.

  in SQL Server:\
  ![image](https://user-images.githubusercontent.com/51430523/138219013-2f52742a-86c7-4583-bdeb-12f0d7a16bc2.png)\
  in MS Access:\
  ![image](https://user-images.githubusercontent.com/51430523/138219120-291db12f-d315-4937-98ab-ba4d715520ff.png)

- `IN`\
  可以嵌套一个SELECT语句.\
  for example:
  ```
  SELECT ... FROM table1
  WHERE ... IN (SELECT ... FROM table2)
  
  ```

- `BEWEEN...AND...`\
  inclusive: begin and end values are included.\
  The values can be: numbers, *text*, or *dates*.

- SQL aliases\
  ... `AS`\
  ![image](https://user-images.githubusercontent.com/51430523/138220014-368b2b73-ca44-479e-8824-4833c7023da6.png)

- Join
   combine rows from two or more tables, based on a related column between them.\
   ![image](https://user-images.githubusercontent.com/51430523/138220293-bb709ad7-7aae-41d7-9325-e78b667dbdba.png)\
   \
   ![image](https://user-images.githubusercontent.com/51430523/138220372-46133b32-35c6-4754-81a3-4cb20b9696b9.png)

  - inner join\
    selects records that have matching values in both tables.\
    selects all rows from both tables as long as there is a match between the columns.\
    \
    join two tables:\
    ![image](https://user-images.githubusercontent.com/51430523/138220604-bfe6c6d9-a1c7-4b05-95e3-3235327659fd.png)\
    \
    join three tables:\
    ![image](https://user-images.githubusercontent.com/51430523/138220766-6f67ede8-86e7-45cc-ab35-e8cfeea1dfbb.png)

  - left join (left outer join)\
    returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
    
  - right join\
    returns all records from the right table (table2), and the matching records from the left table (table1). 

  - full outer join\
    returns all records when there is a match in left (table1) or right (table2) table records.

  - self join\
    The table is joined with itself.\
    ![image](https://user-images.githubusercontent.com/51430523/138221430-66bb726d-3e0c-4027-98a5-7e09d3c8650f.png)

- `UNION`\
  used to combine the result-set of two or more SELECT statements.\
  must have the same number of columns, in same order.\
  The columns must also have similar data types.
  - `UNION`\
    selects only **distinct** values by default.\
    ![image](https://user-images.githubusercontent.com/51430523/138356021-2f9ff849-e828-4460-8494-9e1ac22bde22.png)

  - `UNION ALL`\
    Also allow **duplicate** values.\
    ![image](https://user-images.githubusercontent.com/51430523/138356087-d04db143-9d94-4711-b215-a0b0738c1a3a.png)

- `GROUP BY`\
  ![image](https://user-images.githubusercontent.com/51430523/138356588-c9356c47-733b-4106-a53b-a7cefd1403bb.png)\
  often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

- `HAVING`\
  The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.\
  ![image](https://user-images.githubusercontent.com/51430523/138357104-e1d54dd6-1b7b-41c1-8565-a28acbfc1d83.png)
  example:\
  ![image](https://user-images.githubusercontent.com/51430523/138357162-2ef57fed-c008-419b-b105-4e10fe6b3650.png)

- `EXISTS`\
  test for the existence of any record in a subquery.\
  returns TRUE if the subquery returns one or more records.  \
  ![image](https://user-images.githubusercontent.com/51430523/138357337-3c8ff65d-cd74-42c0-9619-f593d7b50c4c.png)\
  \
  ![image](https://user-images.githubusercontent.com/51430523/142775292-65c288d7-a9c2-459e-89cb-f6aeb0a3949b.png)


- `ANY`\
  perform a comparison between a single column value and a range of other values.\
  returns a boolean value as a result.\
  returns TRUE if ANY of the subquery values meet the condition.\
  The operator must be a standard comparison operator (=, <>, !=, >, >=, <, or <=).\
  ![image](https://user-images.githubusercontent.com/51430523/138357597-4dd2cdf3-fad9-49d4-8c68-a5604f9f9e55.png)

- `ALL` \  
  returns a boolean value.\
  returns TRUE if ALL of the subquery values meet the condition.\
  is used with SELECT, WHERE and HAVING statements.\
  ![image](https://user-images.githubusercontent.com/51430523/138357711-ea055606-0bb3-4bf9-8148-278f7aa55eae.png)
  ![image](https://user-images.githubusercontent.com/51430523/138357755-0a3434a3-b2ff-452a-aeb0-46d0e375e1b2.png)\
  The operator must be a standard comparison operator (=, <>, !=, >, >=, <, or <=).
  
- `SELECT INTO`\
  copies data from one table into a new table.\
  New table inherits old table's data type and schema.\
  ![image](https://user-images.githubusercontent.com/51430523/138358086-7988bf3d-9bda-451e-8ac9-87a80569029a.png)
  - SELECT INTO can also be used to create a new, empty table using the schema of another. Just add a WHERE clause that causes the query to return no data:\
    ![image](https://user-images.githubusercontent.com/51430523/138358306-34eb3f2f-558b-4d32-9d80-b5e160dafd47.png)

- `INSERT INTO SELECT`\
  copies data from one table and inserts it into another table.\
  requires that the data types in source and target tables matches.\
  The existing records in the target table are unaffected.\
  ![image](https://user-images.githubusercontent.com/51430523/138358595-f09d5f77-8e56-4511-a4f3-dc5edb2767d8.png)

- `CASE`\
  goes through conditions and returns a value when the first condition is met (like an if-then-else statement). \
  once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.\
  If there is no ELSE part and no conditions are true, it returns NULL.\
  ![image](https://user-images.githubusercontent.com/51430523/138358916-04a59c4a-1900-4937-8db0-49ba3a718877.png)\
  \
  example:\
  ![image](https://user-images.githubusercontent.com/51430523/138359066-c6131f0e-baa9-4f9f-a5a3-ea085a866d78.png)

- NULL functions
  - `IFNULL()`\
    `IFNULL(expression, alt_value)`
  - `ISNULL()`\
    `ISNULL(expression, value)`\
    if the expression is NULL, return the value; if not null, return the expression.
  - `COALESCE()`\
    `COALESCE(val1, val2, ...., val_n)`\
    returns the first non-null value in a list.
  - `NVL()`\
  \
  MySQL:\
  ![image](https://user-images.githubusercontent.com/51430523/138359276-f1ab1681-8f1a-4a6a-8289-0f1501927e29.png)\
  \
  SQL Server:\
  ![image](https://user-images.githubusercontent.com/51430523/138359370-7195519f-0aa3-4ca7-bb88-f6a94b02691d.png)\
  \
  MS Access:\
  ![image](https://user-images.githubusercontent.com/51430523/138359484-8d9186a7-10c2-431d-9557-52a67a531d40.png)\
  \
  Oracle:\
  ![image](https://user-images.githubusercontent.com/51430523/138359539-5dcd5c0d-510f-44f1-843e-3d125d0c6fbe.png)

### Date-Related

- `BETWEEN date1 AND date2`:\
  start and end *inclusive*.\
  Thus, if X day duration, either date should be `SUBDATE(date2, INTERVAL (X-1) DAY)`.
  
# Stored Procedure
a prepared SQL code that you can save, so the code can be reused over and over again.\
\
Creation:\
![image](https://user-images.githubusercontent.com/51430523/138360454-d9a11884-2b5a-48b3-b084-5ba8cf5111b3.png)\
\
Execution:\
![image](https://user-images.githubusercontent.com/51430523/138360517-ff449935-890b-4ead-aa73-9c3c91afdefa.png)

- Stored Procedure With Multiple Parameters\
list each parameter and the data type separated by a comma as shown below. \
\
![image](https://user-images.githubusercontent.com/51430523/138360788-2ae62e4a-a3ce-4276-9747-014ee69405bf.png)
![image](https://user-images.githubusercontent.com/51430523/138360822-0bd4868f-cc0f-459e-a498-8d0a6386c7a6.png)

# Comment
- Single line comment\
  Single line comments start with `--`.
  Any text between -- and the end of the line will be ignored (will not be executed).\
  ![image](https://user-images.githubusercontent.com/51430523/138361100-ccbabc9e-1c37-4250-a682-34465d624ec8.png)
- Multi-line Comments
  ```
  /*
  
    */
  ```

# SQL Operators
  [link](https://www.w3schools.com/sql/sql_operators.asp)
  
  ## bitwise operators:
  ![image](https://user-images.githubusercontent.com/51430523/138361402-d2f1741d-e024-4180-8c02-ebf89fdda293.png)
  - ^ (bitwise exclusive or)\
  "XOR"\
  different from "OR".\
  If both bits are 1 's or both bits are 0 's, the corresponding bit of the result is set to 0. (when two bits are the same it returns you 0 instead.)
  - `SOME`, `ANY` are interchangeble
  
  
  
  
