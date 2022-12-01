

## 数据表

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
product_id 是这个表的主键。
low_fats 是枚举类型，取值为以下两种 ('Y', 'N')，其中 'Y' 表示该产品是低脂产品，'N' 表示不是低脂产品。
recyclable 是枚举类型，取值为以下两种 ('Y', 'N')，其中 'Y' 表示该产品可回收，而 'N' 表示不可回收。
```



## 要求

```
查找既是低脂又是可回收的产品编号。
```



## MyVerison

```
select product_id from Products p
where p.low_fats = 'Y' and p.recyclable = 'Y'
```



## OtherVersion

```
https://leetcode.cn/problems/recyclable-and-low-fat-products/solutions/602968/xin-nian-kuai-le-by-richard-95-s11o/?orderBy=hot


超多种用法，需要后期深入了解实践。
```

