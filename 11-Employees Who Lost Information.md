## 数据库

```
表: Employees

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
+-------------+---------+
employee_id 是这个表的主键。
每一行表示雇员的id 和他的姓名。

表: Salaries

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| salary      | int     |
+-------------+---------+
employee_id is 这个表的主键。
每一行表示雇员的id 和他的薪水。


Employees table:
+-------------+----------+
| employee_id | name     |
+-------------+----------+
| 2           | Crew     |
| 4           | Haven    |
| 5           | Kristian |
+-------------+----------+
Salaries table:
+-------------+--------+
| employee_id | salary |
+-------------+--------+
| 5           | 76071  |
| 1           | 22517  |
| 4           | 63539  |
+-------------+--------+
```



## 要求

```
写出一个查询语句，找到所有 丢失信息 的雇员id。当满足下面一个条件时，就被认为是雇员的信息丢失：

雇员的 姓名 丢失了，或者
雇员的 薪水信息 丢失了，或者
返回这些雇员的id  employee_id ， 从小到大排序 。

+-------------+
| employee_id |
+-------------+
| 1           |
| 2           |
+-------------+
```



## MyVersion

```
select 
    employee_id 
from 
    (
    select employee_id from employees
    union all 
    select employee_id from salaries
) as t
group by 
    employee_id
having 
    count(employee_id) = 1
order by 
    employee_id;
```

```
union 和 union all都可以起到关联结果集的作用, union 会自动去除关联的两个结果集中的重复数据 union all 不会主动去除两个结果集中的重复数据,会展示所有的数据
```



## OtherVersion

```

```

