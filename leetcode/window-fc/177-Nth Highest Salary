# 题目名称
Nth Highest Salary
## 题目描述
编写一个解决方案查询Employee表中第n高的不同工资。如果少于n个不同工资，查询结果应该为null

## 我的思路
176变体，还是看到排序就想到窗口

## 解法
```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
  RETURN (
     SELECT MAX(salary) AS getNthHighestSalary
     FROM (
        SELECT salary, DENSE_RANK () OVER (ORDER BY salary) AS rnk
        FROM Employee
     )t
     WHERE rnk = N
  );
END
```

## 踩坑 & 感想
暂无
