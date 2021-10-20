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


