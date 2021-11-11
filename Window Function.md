# Window Function

aka. **Online Anallytical Processing function (OLAP)**  
联机分析处理

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
在上述的这三个专用窗口函数中，函数后面的括号不需要任何参数，保持()空着就可以。\
\
![image](https://user-images.githubusercontent.com/51430523/141248528-6aa729ba-9da6-4feb-9e7e-a55ed02465d1.png)\


## Functionality

窗口函数有以下功能：\
\
1）同时具有group by分组, order by排序的功能\
2）不减少原表的行数

## Mindset
窗口函数具备了我们之前学过的group by子句分组的功能和order by子句排序的功能。那么，为什么还要用窗口函数呢？\
这是因为，group by分组汇总后改变了表的行数，一行只有一个类别。而partiition by和rank函数不会减少原表中的行数。\
\
例如:统计每个班级的人数\
![image](https://user-images.githubusercontent.com/51430523/141248723-b90393d9-56d6-463c-8a21-502bf6c8ea6b.png)



## References
[window function 猴子数据分析](https://mp.weixin.qq.com/s?__biz=MzAxMTMwNTMxMQ==&mid=2649247566&idx=1&sn=f9c7018c299498673b38221db2ecd5cd&chksm=835fc77eb4284e68b7528fd7f75eedb8868a6740704af8559f8a5cbdd2867a49ffa21bf4e531&token=426730634&lang=zh_CN#rd)