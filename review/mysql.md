
## MYSQL
### 1,mysql优化
(1) sql 查询优化，先唯一索引=,一般索引=,唯一索引范围,一般索引范围

name是唯一索引，region_id是普通索引，region_id=1200的记录有11条
```
$ explain select * from t_street_copy where name<'农' and region_id=1200;

+----+-------------+---------------+------+---------------+------------+---------+-------+------+-------------+
| id | select_type | table         | type | possible_keys | key        | key_len | ref   | rows | Extra       |
+----+-------------+---------------+------+---------------+------------+---------+-------+------+-------------+
|  1 | SIMPLE      | t_street_copy | ref  | idx_region    | idx_region | 5       | const |   11 | Using index |
+----+-------------+---------------+------+---------------+------------+---------+-------+------+-------------+
```  
(2)MySQL 的索引和最左前缀原则 [链接](https://www.cnblogs.com/jamesbd/p/4333901.html)

(3)什么是回表？  
    简单来说就是数据库根据索引找到了指定的记录所在行后，还需要根据rowid再次到数据块里取数据的操作；  
### 2,mysql事务隔离级别  [链接](https://www.cnblogs.com/huanongying/p/7021555.html)
* 事务基本要素：一致性，原子性，隔离性，持久性
* 隔离级别：读未提交，不可重复读，可重复读，串行话
* Innodb锁的算法：  
  1,Record Lock: 但个行记录的锁   
  2,GAP Lock: 间隙锁,锁定一个范围,但不包含记录本身   
  3,Next-Key Lock: Gap Lock+Record Lock 锁定一个范围并锁定记录本身  


### mysql explain用法和结果的含义[链接](https://www.cnblogs.com/yycc/p/7338894.html)



### 参考
* [Mysql 索引优化分析](https://www.yanshuo.me/p/133130)
* [MySQL 执行计划(Using where,Using index 和 Using index condition)](https://blog.csdn.net/z69183787/article/details/53393153)
