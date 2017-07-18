# MYSQL性能调优与架构设计  

## Chapter 1，MYSQL基本介绍
* MySQL 是由 MySQL AB 公司（目前已经被 SUN 公司收归麾下）自主研发的，目前 IT 行业
最流行的开放源代码的数据库管理系统之一，它同时也是一个支持多线程高并发多用户的关
系型数据库管理系统。  
* 1985 年，瑞典的几位志同道合小伙子（以 David Axmark 为首） 成立了一家公司，这
就是 MySQL AB 的前身。   
* 在最初，他们只是自己设计了一个利用索引顺序存取数据的方法，也就是 I S A M（Indexed
Sequential Access Method）存储引擎核心算法的前身，利用 ISAM 结合 mSQL 来实现他们的
应用需求。
* 在 2000 年的时候，MySQL 公布了自己的源代码，并采用 GPL（GNU General Public
License）许可协议，正式进入开源世界。  

* MySQL的三个原则：简单、高效、可靠。  

### MySQL 的主要适用场景
* Web 网站系统
* 日志记录系统
* 数据仓库系统
* 嵌入式系统

## 2，MYSQL架构组成
### 2.1 物理文件组成
MYSQL的物理文件主要有 日志文件、数据文件、Replication相关文件。
#### 日志文件
* 1、错误日志：Error Log  
* 2、二进制日志：Binary Log & Binary Log Index  
    **二进制日志，也就是我们常说的 binlog，也是 MySQL Server 中最为重要的日志之一。**
当我们通过“--log-bin[=file_name]”打开了记录的功能之后，MySQL 会将所有修改数据
库数据的 query 以二进制形式记录到日志文件中。当然，日志中并不仅限于 query 语句这么
简单，还包括每一条 query 所执行的时间，所消耗的资源，以及相关的事务信息，所以 binlog
是事务安全的。
* 4、查询日志：query log
* 5、慢查询日志：slow query log
* 6、Innodb 的在线 redo 日志：innodb redo log
## 3，MYSQL存储引擎简介
## 4，MYSQL安全管理
## 5，MYSQL备份与恢复
