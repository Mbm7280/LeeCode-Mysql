## 数据库

```

表： Weather

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id 是这个表的主键
该表包含特定日期的温度信息

+----+------------+-------------+
| id | recordDate | Temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
```



## 要求

```
编写一个 SQL 查询，来查找与之前（昨天的）日期相比温度更高的所有日期的 id 。
返回结果 不要求顺序 。

+----+
| id |
+----+
| 2  |
| 4  |
+----+
```



## MyVersion

```
SELECT b.Id
FROM Weather as a,Weather as b
WHERE a.Temperature < b.Temperature and DATEDIFF(a.RecordDate,b.RecordDate) = -1;
```



## 题解

```
DATEDIFF 函数，可以计算两者的日期差
	DATEDIFF('2007-12-31','2007-12-30');   # 1
	DATEDIFF('2010-12-30','2010-12-31');   # -1
```



## OtherVersion

```

```

