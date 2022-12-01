

## 数据表

```
Customers 表：

+----+-------+
| Id | Name  |
+----+-------+
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |
+----+-------+
Orders 表：

+----+------------+
| Id | CustomerId |
+----+------------+
| 1  | 3          |
| 2  | 1          |
+----+------------+
```



## 要求

```
编写一个 SQL 查询，找出所有从不订购任何东西的客户。
```



## MyVersion

```
select cs.name as 'Customers'
from customers cs
where cs.id not in
(
    select customerid from orders
);
```





## OtherVersion （左连接）

```
SELECT
	a.NAME AS Customers 
FROM
	Customers AS a
	LEFT JOIN Orders AS b ON a.Id = b.CustomerId 
WHERE
	b.CustomerId IS NULL;

```

