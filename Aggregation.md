# Aggregation 

### Question List
Check Leetcode SQL 50 Plan list.

### Notes

- Check which column is used to be the unique column in result table:\
  Catch key word **"for each xxxx"**.\
  Then, use the table with this unique column to `LEFT JOIN` another table + `GROUP BY` this unique column.

- When do rate or percentage calculation in `SELECT` statement:
  
  Check if "percentage" need to multiply 100.
  
  Since we have `GROUP BY` the unique column:
  - Check rate calculation, if in group aggregation is needed, use key words (like `SUM()`, `COUNT()`) directly on columns: inside `()`, use columns or boolean statement.
  - Check rate calculation, if outside group or total aggregation is needed, use a separate `SELECT` statement to get data from whole pictures.
  
