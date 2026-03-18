# 176. Second Highest Salary

## 题目
查询并返回 Employee 表中第二高的不同薪水 。如果不存在第二高的薪水，查询应该返回 null(Pandas 则返回 None) 。

## 我的思路
1. 看到排名第一反应窗口函数排序，因此直接使用
2. 也可以使用子查询，但是子查询相对来说比较难以理解
## 解法
1. 窗口函数解法
```sql
SELECT MAX(salary) AS SecondHighestSalary
FROM (
    SELECT salary,
    DENSE_RANK () OVER (ORDER BY salary DESC)AS rnk
    FROM Employee
)t
WHERE rnk = 2
```
2. 子查询写法
```sql
SELECT (
    SELECT DISTINCT salary
    FROM Employee
    ORDER BY salary DESC
    LIMIT 1 OFFSET 1
) AS SecondHighestSalary
```

## 踩坑 & 感想
1. 不存在则返回 null
  MAX() 的特性：它是一个聚合函数。如果你对一个空集（没有任何行）执行 MAX()，SQL 规定它的返回值是 NULL。
  DISTINCT 的特性：它只是一个过滤修饰符。如果你对一个空集执行 DISTINCT，结果依然是空集（0 行数据），它不会凭空变出一个 NULL 来

2. SQL 逻辑执行顺序模板
FROM-> ON-> JOIN-> WHERE-> GROUP BY-> WITH ROLLUP / CUBE-> HAVING-> WINDOW (窗口函数)-> SELECT-> DISTINCT-> ORDER BY-> LIMIT / OFFSET
