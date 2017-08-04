* MySQL的InnoDB索引原理详解 http://www.cnblogs.com/shijingxiang/articles/4743324.html  
* 数据行长度的一些限制 http://www.cnblogs.com/zhiqian-ali/p/5037317.html

## Mysql 两种索引结构  
1，B+Tree  
2，Hash  

## Mysql 常见索引：  
1，主键索引  
2，唯一索引  
3，普通索引  
4，全文索引  
5，组合索引  

## Mysql 索引区别  
普通索引：最基本的索引，没有任何限制  
唯一索引：与"普通索引"类似，不同的就是：索引列的值必须唯一，但允许有空值。  
主键索引：它 是一种特殊的唯一索引，不允许有空值。   
全文索引：仅可用于 MyISAM 表和MYSQL5.6 Innodb，针对较大的数据，生成全文索引很耗时耗空间。  
组合索引：为了更多的提高mysql效率可建立组合索引，遵循”最左前缀“原则。  
  
