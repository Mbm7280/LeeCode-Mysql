## 数据库

```
表: SalesPerson

+-----------------+---------+
| Column Name     | Type    |
+-----------------+---------+
| sales_id        | int     |
| name            | varchar |
| salary          | int     |
| commission_rate | int     |
| hire_date       | date    |
+-----------------+---------+
sales_id 是该表的主键列。
该表的每一行都显示了销售人员的姓名和 ID ，以及他们的工资、佣金率和雇佣日期。

表: Company

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| com_id      | int     |
| name        | varchar |
| city        | varchar |
+-------------+---------+
com_id 是该表的主键列。
该表的每一行都表示公司的名称和 ID ，以及公司所在的城市。

表: Orders

+-------------+------+
| Column Name | Type |
+-------------+------+
| order_id    | int  |
| order_date  | date |
| com_id      | int  |
| sales_id    | int  |
| amount      | int  |
+-------------+------+
order_id 是该表的主键列。
com_id 是 Company 表中 com_id 的外键。
sales_id 是来自销售员表 sales_id 的外键。
该表的每一行包含一个订单的信息。这包括公司的 ID 、销售人员的 ID 、订单日期和支付的金额。

SalesPerson 表:
+----------+------+--------+-----------------+------------+
| sales_id | name | salary | commission_rate | hire_date  |
+----------+------+--------+-----------------+------------+
| 1        | John | 100000 | 6               | 4/1/2006   |
| 2        | Amy  | 12000  | 5               | 5/1/2010   |
| 3        | Mark | 65000  | 12              | 12/25/2008 |
| 4        | Pam  | 25000  | 25              | 1/1/2005   |
| 5        | Alex | 5000   | 10              | 2/3/2007   |
+----------+------+--------+-----------------+------------+
Company 表:
+--------+--------+----------+
| com_id | name   | city     |
+--------+--------+----------+
| 1      | RED    | Boston   |
| 2      | ORANGE | New York |
| 3      | YELLOW | Boston   |
| 4      | GREEN  | Austin   |
+--------+--------+----------+
Orders 表:
+----------+------------+--------+----------+--------+
| order_id | order_date | com_id | sales_id | amount |
+----------+------------+--------+----------+--------+
| 1        | 1/1/2014   | 3      | 4        | 10000  |
| 2        | 2/1/2014   | 4      | 5        | 5000   |
| 3        | 3/1/2014   | 1      | 1        | 50000  |
| 4        | 4/1/2014   | 1      | 4        | 25000  |
+----------+------------+--------+----------+--------+
```



## 要求

```
编写一个SQL查询，报告没有任何与名为 “RED” 的公司相关的订单的所有销售人员的姓名。


```



## MyVersion

```
-- 子查询(效率低)
SELECT
    s.name
FROM
    salesperson s
WHERE
    s.sales_id NOT IN (SELECT
            o.sales_id
        FROM
            orders o
                LEFT JOIN
            company c ON o.com_id = c.com_id
        WHERE
            c.name = 'RED')
;
```



## 题解

```

```



## OtherVersion

```
-- 不使用子查询，一次SELECT()
-- IF(C.name = 'RED', 1, 0) 如果C.name = 'RED'计数为1，否则计数为0 
-- 前边GROUP BY S.name后 加SUM( )=0确保该销售员一次也没和RED交易过
SELECT
    S.name
FROM
    salesperson S
    LEFT JOIN
    orders O ON S.sales_id = O.sales_id
    LEFT JOIN
    company C ON O.com_id = C.com_id
GROUP BY
    S.name
HAVING
    SUM(IF(C.name = 'RED', 1, 0))  = 0
ORDER BY
    S.sales_id
```

