## SQL优化案例
### 1，not in 子查询优化  
解决方案：可用left join 表连接取代。
```
mysql> select * from test1 where id not in (select id from test2);
```
替换成
```
mysql> select * from test1 left join test2 on test1.id=test2.id where test2.id is null;
```

### 2，模式匹配 like '%xxx%' 优化  
在MySQL 里， like 'xxx%' 可以用到索引，但like '%xxx%' 不能。

### 3，limit 分页优化  
### 4，count(*)统计数据  
where 条件最好是走索引，  
count(distinct) 优化  
distinct 字段索引

## 5，OR 条件如何优化
OR 条件不会走索引，全表扫描   改用 union all结果合并
```
select * from user where name='xx' or phone=13812345678;
```
改成
```
select * from user where name='xx' union all select * from user where phone=13812345678;
```

## 6，使用ON DUPLICATE KEY UPDATE 子句
MYSQL 中有一种非常高效的主键冲突处理判断，冲突则执行update,不冲突则执行insert逻辑的语句：
ON DUPLICATE KEY UPDATE,例如：
insert into relation(`key`,`column1`) values('xiao',1) on duplicate key update column1=column1+1;
> 注：key唯一索引

## 7，去掉不必要的排序
## 8，优化不必要的嵌套select查询 , 改成 join
## 9, 不必要的表自身链接
## 10，用where 子句替换having子句

# 合理使用索引
1，联合索引要遵循最左侧原则  
2，字段使用函数，将不能使用索引  
3，致命的无引号导致全表扫描，无法引用索引  
4，当去除的数据量超过表中数据的20%,优化器就不会使用索引，而是全表扫描  
5，考虑不为某些列建立索引 例如男、女，是、否 这种均匀分布的值  
6，order by ,group by 优化，  
一条SQL只能有一个索引，如果有多条索引，优化器会选择最有的，  
```
select * from `test_change` where pid= 20170803 order by change_date
```
可以建立一个`pid` 和 `change_date` 的联合索引  
order by 后有多个字段，他么的顺序要一致，如果一个是降序，一个是升序，也会出现Using filesort排序  
7,MySQL5.6 支持explain update/delete  
8,MYSQL5.6 InnoDB 引擎支持全文索引  
9，MYSQL5.6 支持Multi-Range Read 索引优化  
MYSQL5.6 优化器会先扫描索引，然后收集每行的主键，并对主键排序，此时就可以用主键顺序访问基表，即用顺序I/O代替了随机I/O.  
10,MYSQL5.6 优化了Index Merge 合并索引，也就是说一条SQL可以用上两个索引了。  
