# Window Function

aka. **Online Anallytical Processing function (OLAP)**  
联机分析处理

## window function原则上只能写在select子句中

## conditions
1. ranking
2. top N
3. find consecutive N times items

[find consecutive N times items 找出连续出现N次的内容](https://mp.weixin.qq.com/s?__biz=MzAxMTMwNTMxMQ==&mid=2649250661&idx=1&sn=b017344c701fbfa02a87a88a1a2207cd&chksm=835fd355b4285a43d6c55c593f83bbc7aea1bb370df8f52210bb3b3f7f5c5f304c272d863a04&token=546838497&lang=zh_CN#rd)

window functions, which are accessed via the OVER clause. 

[MySQL OVER clause](https://learnsql.com/blog/over-clause-mysql/)

## Syntax
![image](https://user-images.githubusercontent.com/51430523/141248141-04691493-f800-4fc6-9092-66bba5240ae2.png)

![image](https://user-images.githubusercontent.com/51430523/141248351-69ee976c-d9fd-48bc-babd-1e57f3cb4b99.png)\

- Aggregation function聚合函数

![image](https://user-images.githubusercontent.com/51430523/223164310-5fb99d40-2f3b-43ef-8a5c-85b2d652e45a.png)

聚合函数在窗口函数中，是对自身记录、及位于自身记录以上的数据进行求和的结果:\
![image](https://user-images.githubusercontent.com/51430523/223164916-d7db36b0-4cd9-4847-bb2f-6c948f849613.png)

aggregation window function 后面括号里面不能为空，需要指定聚合的列名。\
聚合函数作为窗口函数，可以在每一行的数据里直观的看到，截止到本行数据，统计数据是多少（最大值、最小值等）。同时可以看出每一行数据，对整体统计数据的影响。\
\
example:\
![image](https://user-images.githubusercontent.com/51430523/141249467-307a991e-a4ef-4d0a-8363-cc12671dce56.png)\

- Specific Window Function

**RANK, DENSE_RANK, ROW_NUMBER**

在上述的这三个专用窗口函数中，函数后面的括号不需要任何参数，保持()空着就可以。\
\
![image](https://user-images.githubusercontent.com/51430523/141248528-6aa729ba-9da6-4feb-9e7e-a55ed02465d1.png)\


## Functionality

窗口函数有以下功能：\
\
1）同时具有partition by分组, order by排序的功能\
2）不减少原表的行数

## Mindset
窗口函数具备了我们之前学过的group by子句分组的功能和order by子句排序的功能。那么，为什么还要用窗口函数呢？\
这是因为，group by分组汇总后改变了表的行数，一行只有一个类别。而partiition by和rank函数不会减少原表中的行数。\
\
例如:统计每个班级的人数\
![image](https://user-images.githubusercontent.com/51430523/141248723-b90393d9-56d6-463c-8a21-502bf6c8ea6b.png)



## References
[window function 猴子数据分析](https://mp.weixin.qq.com/s?__biz=MzAxMTMwNTMxMQ==&mid=2649247566&idx=1&sn=f9c7018c299498673b38221db2ecd5cd&chksm=835fc77eb4284e68b7528fd7f75eedb8868a6740704af8559f8a5cbdd2867a49ffa21bf4e531&token=426730634&lang=zh_CN#rd)
