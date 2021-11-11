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
\
![image](https://user-images.githubusercontent.com/51430523/141243056-829ebac3-9591-413c-b8b4-c990bd824301.png)
