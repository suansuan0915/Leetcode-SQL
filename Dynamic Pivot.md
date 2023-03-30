## Dynamic Pivot Tables in MySQL

- pivot:\
*Q2252. Dynamic Pivoting of a Table*
*1777. Product's Price for Each Store*
- unpivot:\
*1795. Rearrange Products Table*

"Pivot":\
from rows to columns.

When creating pivot tables in SQL:
- Use `CASE WHEN` clause: only if we know all the columns we need to create in a pivot table.
- Use `GROUP_CONCAT` function: to dynamically transpose rows to columns (when we don't know exact columns).

### Methodology

we use GROUP_CONCAT to dynamically create CASE statements, 
based on unique values in the field_key column and store that string in @sql variable. It is then used to create our select query.

```
## Override GROUP_CONCAT length which has a default limit of 1024
# session-scope: only applies to the current session
SET SESSION group_concat_max_len=1000000;

SET @case_stmt = null;
SELECT GROUP_CONCAT(
  DISTINCT CONCAT('CASE WHEN store = "', store, '" THEN price END AS ', store)
  )  
INTO @case_stmt
FROM Products;

SET @query = CONCAT('SELECT product_id, ', @case_stmt, ' FROM Products GROUP BY product_id');

PREPARE final_query FROM @query;
EXECUTE final_query;
DEALLOCATE PREPARE final_query;
```

### Attention
In `CONCAT()`:\
must leave necessary space before/after some keywords, \
for example:\
`CONCAT('CASE WHEN store = "', store, '" THEN price END AS ', store)` leave a space after `AS`.\
`SET @query = CONCAT('SELECT product_id, ', @case_stmt, ' FROM Products GROUP BY product_id');` leave a space before `FROM`.
