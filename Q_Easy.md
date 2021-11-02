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
