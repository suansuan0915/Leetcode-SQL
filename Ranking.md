# Ranking

[ranking problems](https://leetcode-cn.com/problems/rank-scores/solution/tu-jie-sqlmian-shi-ti-jing-dian-pai-ming-wen-ti-by/)\
[window function](https://mp.weixin.qq.com/s?__biz=MzAxMTMwNTMxMQ==&mid=2649247566&idx=1&sn=f9c7018c299498673b38221db2ecd5cd&chksm=835fc77eb4284e68b7528fd7f75eedb8868a6740704af8559f8a5cbdd2867a49ffa21bf4e531&token=426730634&lang=zh_CN#rd)

ranking\
-> **window function**\
\
mysql版本8已至此窗口函数这个功能，虽然在leetcode上运行不成功，可能的原因是后台的mysql数据库版本不是最新的。

### Difference

- `RANK`\
  produces ranks with gaps.
- `DENSE_RANK`\
  produces ranks w/o gaps.
- `ROW_NUMBER`\
  排名是序号 连续 不重复，即使遇到表中的两个一样的数值亦是如此.
- `ntile`\
  `ntile(group_num)` 将所有记录分成group_num个组，每组序号一样.
\
![image](https://user-images.githubusercontent.com/51430523/141243056-829ebac3-9591-413c-b8b4-c990bd824301.png)

## ROW_NUMBER function
over子句中的order by 要与SQL排序记录中的order by保持一致，否则得到的序号可能不是连续的:\
\
![image](https://user-images.githubusercontent.com/51430523/141244132-2a907f41-d712-4fe4-b8fd-7e2d98d6a322.png)

![image](https://user-images.githubusercontent.com/51430523/141244208-dad1c011-025d-40c8-abe2-c909dd458ba5.png)

