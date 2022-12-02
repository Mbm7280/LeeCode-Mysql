## 数据表

```
+-------------+---------+
| 列名        | 类型     |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
| salary      | int     |
+-------------+---------+

Employees 表:
+-------------+---------+--------+
| employee_id | name    | salary |
+-------------+---------+--------+
| 2           | Meir    | 3000   |
| 3           | Michael | 3800   |
| 7           | Addilyn | 7400   |
| 8           | Juan    | 6100   |
| 9           | Kannon  | 7700   |
+-------------+---------+--------+
```



## 要求

```
计算每个雇员的奖金。如果一个雇员的id是奇数并且他的名字不是以'M'开头，那么他的奖金是他工资的100%，否则奖金为0。
返回的结果集请按照employee_id排序
```





## MyVersion

```
select employee_id,
if(
    employee_id&1 and name not like 'M%',
    salary,
    0
) as bonus
from employees 
order by employee_id
```



## OtherVersion

```
select
    employee_id,
    if(
        employee_id&1 and name regexp '^[^M]',
        salary,
        0
    ) as bonus
from employees
order by employee_id;
```

