# 题目名称
Rank Scores
## 题目描述
分数应按从高到低排列。
如果两个分数相等，那么两个分数的排名应该相同。
在排名相同的分数后，排名数应该是下一个连续的整数。换句话说，排名之间不应该有空缺的数字。
按 score 降序返回结果表。

## 我的思路
看到排名就（qwq）

## 解法
```sql
SELECT score, DENSE_RANK () OVER (ORDER BY score DESC) AS 'rank'
FROM Scores
```

## 踩坑 & 感想
坑就是，rank是有特殊含义的，想要列名是rank需要加引号
