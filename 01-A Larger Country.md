```
2022年12月01日23:14:40
```



## 数据表

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | int     |
+-------------+---------+
name 是这张表的主键。
这张表的每一行提供：国家名称、所属大陆、面积、人口和 GDP 值。
```



## 条件

```
如果一个国家满足下述两个条件之一，则认为该国是 大国 ：

面积至少为 300 万平方公里（即，3000000 km2），或者
人口至少为 2500 万（即 25000000）
编写一个 SQL 查询以报告 大国 的国家名称、人口和面积。

按 任意顺序 返回结果表。
```



## myVersion

```
select name,population,area from world w
where w.area >= 3000000 or w.population >= 25000000
```



## otherVersion 1 (union)

```
SELECT
    name, population, area
FROM
    world
WHERE
    area >= 3000000

UNION

SELECT
    name, population, area
FROM
    world
WHERE
    population >= 25000000
;

```

使用 or 会使索引会失效，在数据量较大的时候查找效率较低，通常建议使用 union 代替 or。

