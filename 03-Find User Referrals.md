

## 数据表

```
+------+------+-----------+
| id   | name | referee_id|
+------+------+-----------+
|    1 | Will |      NULL |
|    2 | Jane |      NULL |
|    3 | Alex |         2 |
|    4 | Bill |      NULL |
|    5 | Zack |         1 |
|    6 | Mark |         2 |
+------+------+-----------+
```



## 要求

```
写一个查询语句，返回一个客户列表，列表中客户的推荐人的编号都 不是 2。
```

## MyVersion

```
select name from customer c
where c.referee_id != 2 or c.referee_id is null
```



## OtherVersion

```
SELECT name 
 FROM customer 
WHERE referee_id <> 2
UNION ALL
SELECT name 
 FROM customer 
WHERE referee_id IS NULL.

```

