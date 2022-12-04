## 数据库

```
表：Products

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| store1      | int     |
| store2      | int     |
| store3      | int     |
+-------------+---------+
这张表的主键是product_id（产品Id）。
每行存储了这一产品在不同商店store1, store2, store3的价格。
如果这一产品在商店里没有出售，则值将为null。

Products table:
+------------+--------+--------+--------+
| product_id | store1 | store2 | store3 |
+------------+--------+--------+--------+
| 0          | 95     | 100    | 105    |
| 1          | 70     | null   | 80     |
+------------+--------+--------+--------+

```



## 要求

```
请你重构 Products 表，查询每个产品在不同商店的价格，使得输出的格式变为(product_id, store, price) 。如果这一产品在商店里没有出售，则不输出这一行。

输出结果表中的 顺序不作要求 。

+------------+--------+-------+
| product_id | store  | price |
+------------+--------+-------+
| 0          | store1 | 95    |
| 0          | store2 | 100   |
| 0          | store3 | 105   |
| 1          | store1 | 70    |
| 1          | store3 | 80    |
+------------+--------+-------+
```



## MyVersion

```
SELECT product_id, 'store1' store, store1 price FROM products WHERE store1 IS NOT NULL
UNION
SELECT product_id, 'store2' store, store2 price FROM products WHERE store2 IS NOT NULL
UNION
SELECT product_id, 'store3' store, store3 price FROM products WHERE store3 IS NOT NULL;
```



## 题解

```
一列一列处理：把“列名”做为新列的value（如本题的store），把原来的value也作为新列（如本题的price），这是一个查询，其他列不要

用union all拼接每一列的结果

注意本题如果这一产品在商店里没有出售，则不输出这一行，所以要原列 is not null的筛选条件

```



## OtherVersion

```

```

