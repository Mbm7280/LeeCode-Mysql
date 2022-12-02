## 数据库

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| email       | varchar |
+-------------+---------+
Person 表:
+----+------------------+
| id | email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+

id是该表的主键列。
该表的每一行包含一封电子邮件。电子邮件将不包含大写字母。
```



## 要求

```
编写一个 SQL 删除语句来 删除 所有重复的电子邮件，只保留一个id最小的唯一电子邮件。
以 任意顺序 返回结果表。 （注意： 仅需要写删除语句，将自动对剩余结果进行查询）
```



## MyVersion

```
-- 将此表与它自身在电子邮箱列中连接起来。
SELECT p1.*
FROM Person p1,
    Person p2
WHERE
    p1.Email = p2.Email AND p1.Id > p2.Id
;

-- 然后我们需要找到其他记录中具有相同电子邮件地址的更大 ID。所以我们可以像这样给 WHERE 子句添加一个新的条件。
SELECT p1.*
FROM Person p1,
    Person p2
WHERE
    p1.Email = p2.Email
;

-- 最终可以将该语句更改为 DELETE
delete 
p1 From Person p1,Person p2
Where p1.email = p2.email and p1.id > p2.id
```



## OtherVersion

```

```

