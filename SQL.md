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

- `SELECT DISTINCT`\
  return only distinct (different) values.\
  ![image](https://user-images.githubusercontent.com/51430523/138033814-d109271b-e8c1-4f59-b976-6c1c582dd4de.png)

- Operators in `WHERE`\
  ![image](https://user-images.githubusercontent.com/51430523/138034050-a00a1068-c885-4763-9a91-05b53f53460c.png)

- `ORDER BY`\
  sort the result-set in ascending or descending order.\
  ![image](https://user-images.githubusercontent.com/51430523/138034256-f2ced13f-dfd7-4911-87c5-61f3a2e455da.png)

- `INSERT INTO`\
  insert new records in a table.\
  ![image](https://user-images.githubusercontent.com/51430523/138034431-17a773e8-cd7b-4eea-9f63-e67a4ace43cb.png)\
  no specified record will have "null" value.\

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
  MySQL: `LIMIT`\
  oracle: `FETCH FIRST n ROWS ONLY`  and  `ROWNUM`\
  ![image](https://user-images.githubusercontent.com/51430523/138037164-f4af0cb9-1f6b-46b8-a566-d0cfcf0e3b34.png)
  ![image](https://user-images.githubusercontent.com/51430523/138037211-425dbb59-99fb-4717-989c-a55815060fec.png)

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
  in SQL Server:\
  ![image](https://user-images.githubusercontent.com/51430523/138219013-2f52742a-86c7-4583-bdeb-12f0d7a16bc2.png)\
  in MS Access:\
  ![image](https://user-images.githubusercontent.com/51430523/138219120-291db12f-d315-4937-98ab-ba4d715520ff.png)

- `IN`\
  可以嵌套一个SELECT语句.\
  for example:\
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



 
  
  
  
  
  
  
  
  
  
  
  
  
  
