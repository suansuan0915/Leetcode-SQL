# 175. Combine Two Tables
[link](https://leetcode.com/problems/combine-two-tables/)

## 考点
left join/ right join/ inner join\
![image](https://user-images.githubusercontent.com/51430523/139915675-cfe7e810-7263-4d5d-bc62-97ce5f2c12df.png)

#### Diagram:
![image](https://user-images.githubusercontent.com/51430523/139915756-cff8598a-7a54-454f-9d66-60edbd6655d2.png)


## Solution
```ruby

SELECT p.firstName AS firstName, p.lastName AS lastName, a.city AS city, a.state AS state
FROM Person p LEFT JOIN Address a
ON p.personID = a.personID;

```


# 196. Delete Duplicate Emails

[Problem](https://leetcode.com/problems/delete-duplicate-emails/)

## Things to notice
- Every derived table must have its own alias\
  每一个派生出来的表都必须有一个自己的别名.\
  因为修改表的时候不能直接查询被修改的表, 所以需要中间表(临时表)过渡。

- `UNION`\
  two things for `UNION` must be two `SELECT` clause, and the unioned table should have an alias.
- `DELETE`
  DELETE xxx FROM table WHERE ...\
  example:
  ```
  DELETE t1 FROM t1 LEFT JOIN t2 ON t1.id=t2.id WHERE t2.id IS NULL;
  ```
  这种DELETE方式很陌生，竟然和SELETE的写法类似。它涉及到t1和t2两张表，DELETE t1表示要删除t1的一些记录，具体删哪些，就看WHERE条件，满足就删；\
  here, t1 left join t2, there can be some l2.id that not match l1.id, so we need to delete "WHERE" clause denotes -> **delete ALL fields in t1 which not match t2.id**.

- `IN` vs. `EXISTS`\
  
  ![image](https://user-images.githubusercontent.com/51430523/140696467-7d04b44e-e9d9-4e32-97e4-c03b97857a15.png)
  
  \
  ![image](https://user-images.githubusercontent.com/51430523/140698088-efd22796-aa52-4fef-a50b-05e3c09262d2.png)\
  the statement returns the values from the main select statement if it is existing in the subquery statement.\
  \
  `SELECT EXISTS (<query statement>);`
  check the existence of the value\
  \
  MySQL EXITS is used to find out whether a particular row is existing in the table or not. \
  MySQL Exists is used with the subquery and returns the rows that are equal to the result returned by the subquery. \
  \
  The statement returns true if the row exists in the table else false. (1 or 0)\
  \
  It is very inefficient to use the EXISTS in the MySQL since EXISTS re-run for every query in the table. So, it is significant to not use the EXISTS condition.

- 查询的子集\
  
  最内层的查询结果还有group by的结果，所以实际上是email和id都有。not in查询的表只可以有一列.\
```
DELETE FROM table
WHERE id NOT IN
    (SELECT p.p_id 
    FROM
        ( SELECT ...
            FROM ...
            ...) AS p)
```

## Solution
- Method 1:\
  [solution link](https://leetcode-cn.com/problems/delete-duplicate-emails/solution/dui-guan-fang-ti-jie-zhong-delete-he-de-jie-shi-by/)\
  ![image](https://user-images.githubusercontent.com/51430523/140692144-6b85d837-421b-432b-a528-311ee2afbd32.png)

```ruby

DELETE p2
FROM Person p1, Person p2
WHERE p1.email = p2.email AND p1.id < p2.id; 

```

- Method 2:\
  ![image](https://user-images.githubusercontent.com/51430523/140693889-1043e311-5eff-4f56-b0be-74a5dfaee7ca.png)
  
```ruby

DELETE FROM Person 
WHERE id NOT IN
    (SELECT p.p_id 
    FROM
        ( SELECT min(id) AS p_id
            FROM Person
            GROUP BY email ) AS p)

```
此时p是一个table，所以要再select一遍其中的id作为id not in where查询的子集！

- Method 3:\
  `EXISTS`
```ruby

delete
from Person a
where not exists
    (
        select Id
        from
            (
                select Email,
                    min(Id) Id
                from Person
                group by Email
            ) b
        where a.Id = b.Id
    )

```



# 1511. Customer Order Frequency

[Problem](https://leetcode.com/problems/customer-order-frequency/)

## Things to notice

- `SUM`/`COUNT` + `CASE...WHEN...END`\
  window function w/ aggregation function

- DATE functions\
  `DATE_FORMAT(date, format)`\
  format a date as specified.

- aggregation in GROUP BY -> use HAVING\
  Use the MySQL HAVING clause with the GROUP BY clause to specify a filter condition for groups of rows or aggregates.\
  - The difference is: \
    WHERE clause filters which rows MySQL selects. \
    *Then* MySQL groups the rows together and aggregates the numbers for your COUNT function.\
    HAVING is like WHERE, BUT only it happens *after* the aggregation value has been computed, so it'll work as you expect.
  
- SQL evaluation order:\
  ![image](https://user-images.githubusercontent.com/51430523/140808063-47f67c9d-531d-4a66-9893-81f565a31c57.png)

- 子查询才需要临时表过渡 (add *alias* to the subquery table!)\
  "subquery":\
  a `SELECT` query nested in another `SELECT` query.\
  usually used in: WHERE, IN, EXISTS, FROM.

## Solutions

```ruby

SELECT c.customer_id AS customer_id, c.name AS name 
    # (CASE WHEN O.o.quantity IS NOT NULL THEN (p.price * o.quantity) 
    #      ELSE 0) AS t_price, 
    # (SELECT EXTRACT (YEAR_MONTH FROM 
    #                    ( SELECT DATE_FORMAT(o.order_date, '%Y-%m-%d') 
    #                     FROM t.order_date))) AS yr_day
FROM
(Product p JOIN Orders o 
ON p.product_id = o.product_id
JOIN Customers c
ON o.customer_id = c.customer_id)   # 子查询才需要临时表过渡！此处不需要～

GROUP BY c.customer_id, c.name
HAVING SUM(
    (CASE WHEN o.order_date LIKE '2020-06-%'
          THEN (p.price * o.quantity) END
     )) >= 100
    AND 
    SUM(
    (CASE WHEN o.order_date LIKE '2020-07-%'
          THEN (p.price * o.quantity) END 
     )) >= 100;

```



# 1179. Reformat Department Table

[Problem](https://leetcode.com/problems/reformat-department-table/)

## Things to notice
- `GROUP BY` & aggregation:\
  把同一group by条件下的所有rows aggregate在一起，然后可以任意access到其中的一行。\
  在MySQL中，允许下面这样的写法:\
  ![image](https://user-images.githubusercontent.com/51430523/140868518-1290d190-2ef3-4ccb-ab0a-36c887bf3e10.png)
  ![image](https://user-images.githubusercontent.com/51430523/140868558-6a29eaeb-ced6-4f61-9cd4-c1784d06e5eb.png)
  ![image](https://user-images.githubusercontent.com/51430523/140868630-cd5b2565-a9db-4092-a0ac-52831e1d156f.png)\
  此时在第一组中，有三条记录，也就是说有三个revenue，那么此时select id, revenue就无法判定应该取哪一个revenue，所以这样的操作在标准SQL中是不允许的，只能通过聚合函数来处理。而MySQL在这里提供了一种便利的方式，却让理解它的工作方式变得更加困难。\
  ![image](https://user-images.githubusercontent.com/51430523/140872150-3ba72a12-4b34-4c1b-a0f1-634986d663d3.png)


## Solutions

"row-to-column" 行转列

```ruby

SELECT id,
    SUM(CASE WHEN month = 'Jan' THEN revenue END) AS Jan_Revenue,
    SUM(CASE WHEN month = 'Feb' THEN revenue END) AS Feb_Revenue,
    SUM(CASE WHEN month = 'Mar' THEN revenue END) AS Mar_Revenue,
    SUM(CASE WHEN month = 'Apr' THEN revenue END) AS Apr_Revenue,
    SUM(CASE WHEN month = 'May' THEN revenue END) AS May_Revenue,
    SUM(CASE WHEN month = 'Jun' THEN revenue END) AS Jun_Revenue,
    SUM(CASE WHEN month = 'Jul' THEN revenue END) AS Jul_Revenue,
    SUM(CASE WHEN month = 'Aug' THEN revenue END) AS Aug_Revenue,
    SUM(CASE WHEN month = 'Sep' THEN revenue END) AS Sep_Revenue,
    SUM(CASE WHEN month = 'Oct' THEN revenue END) AS Oct_Revenue,
    SUM(CASE WHEN month = 'Nov' THEN revenue END) AS Nov_Revenue,
    SUM(CASE WHEN month = 'Dec' THEN revenue END) AS Dec_Revenue
FROM Department
GROUP BY id;

```


# 1757. Recyclable and Low Fat Products

[Problem](https://leetcode.com/problems/recyclable-and-low-fat-products/)

## Things to notice
- ENUM type:\
  a string object with a value chosen from a list of permitted values that are enumerated explicitly in the column specification at table creation time.







