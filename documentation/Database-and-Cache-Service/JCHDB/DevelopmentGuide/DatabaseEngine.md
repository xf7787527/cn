# 数据库引擎

默认情况下，Clickhouse使用自己的数据库引擎，该引擎提供可配置的 表引擎 和 支持所有的SQL语法，除此之外，还可以选择使用 MySQL数据库引擎。

### MySQL引擎

MySQL 引擎用于将远程的 MySQL 服务器中的表映射到 ClickHouse 中，并允许您对表进行 INSERT 和 SELECT 查询，以方便您在 ClickHouse 与 MySQL 之间进行数据交换。

MySQL 数据库引擎会将对其的查询转换为 MySQL 语法并发送到 MySQL 服务器中，因此您可以执行诸如 SHOW TABLES 或 SHOW CREATE TABLE 之类的操作。

但您无法对其执行以下操作：
 - RENAME
 - CREATE TABLE
 - ALTER

 在MySQL中创建表：
 ```SQL
CREATE DATABASE [IF NOT EXISTS] db_name [ON CLUSTER cluster]ENGINE = MySQL('host:port', ['database' | database], 'user', 'password')
 ```

MySQL数据库引擎参数说明：
|参数|说明|
|---|---|
|database|链接的 MySQL 数据库|
|host:port|链接的 MySQL 地址|
|password|链接的 MySQL 用户密码|
|user|链接的 MySQL 用户|

MySQL 和 ClickHouse 支持的类型对应说明：
|MySQL|Clcikhouse|
|---|---|
|UNSIGNED TINYINT|UInt8|
|TINYINT|Int8|
|UNSIGNED SMALLINT|UInt16|
|SMALLINT|Int16|
|UNSIGNED INT, UNSIGNED MEDIUMINT|UInt32|
|INT, MEDIUMINT|Int32|
|UNSIGNED BIGINT|UInt64|
|BIGINT|Int64|
|FLOAT|Float32|
|DOUBLE|Float64|
|DATE|日期|
|DATETIME, TIMESTAMP|日期时间|
|BINARY|固定字符串|

 - 其他的 MySQL 数据类型将全部都转换为 字符串。
 - 同时以上的所有类型都支持 可为空。

*使用示例*

**在MySQL中创建表：**

```SQL
mysql> USE test;Database changed
mysql> CREATE TABLE `mysql_table` (
-> `id` INT NOT NULL AUTO_INCREMENT,
-> `float` FLOAT NOT NULL,
-> PRIMARY KEY (`id`));Query OK, 0 rows affected (0,09 sec)
mysql> insert into mysql_table (`id`, `float`) VALUES (1,2);Query OK, 1 row affected (0,00 sec)
mysql> select * from mysql_table;+--------+-------+| id | value |+--------+-------+| 1 | 2 |+--------+-------+1 row in set (0,00 sec)
```

**在Clickhouse中创建MySQL类型的数据库，同时与MySQL服务器交换数据：**

```SQL
CREATE DATABASE mysql_db ENGINE = MySQL('localhost:3358', 'test', 'my_user', 'user_password')
SHOW DATABASES
┌─name─────┐
│ default │
│ mysql_db │
│ system │
└──────────┘
SHOW TABLES FROM mysql_db
┌─name─────────┐
│ mysql_table │
└──────────────┘
SELECT * FROM mysql_db.mysql_table
┌─int_id─┬─value─┐
│ 1 │ 2 │
└────────┴───────┘
INSERT INTO mysql_db.mysql_table VALUES (3,4)
SELECT * FROM mysql_db.mysql_table
┌─int_id─┬─value─┐
│ 1 │ 2 │
│ 3 │ 4 │
└────────┴───────┘
```

### 表引擎

表引擎即表的类型，在ClickHouse中的作用十分关键，直接决定了数据如何存储和读取、是否支持并发读写、是否支持索引、支持的查询种类、是否支持主备复制等。
ClickHouse提供了多种表引擎，用途广泛。分为MergeTree、Log、Integration、Special四个系列，在这些表引擎之外，ClickHouse还提供了Replicated、Distributed等高级表引擎，功能上与其他表引擎正交，根据场景组合使用。

#### 引擎类型

**MergeTree系列**

适用于高负载任务的最通用和功能最强大的表引擎。这些引擎的共同特点是可以快速插入数据并进行后续的后台数据处理。MergeTree系列的引擎被设计用于插入极大量的数据到一张表当中。数据可以以数据片段的形式一个接着一个的快速写入，数据片段在后台按照一定的规则进行合并。相比在插入时不断修改（重写）已存储的数据，这种策略会高效很多。MergeTree 系列引擎支持数据复制（使用 Replicated* 的引擎版本），分区和一些其他引擎不支持的其他功能。

该类型的引擎：

 - MergeTree
 - ReplacingMergeTree
 - SummingMergeTree
 - AggregatingMergeTree
 - CollapsingMergeTree
 - VersionedCollapsingMergeTree
 - GraphiteMergeTree

**Log系列**

具有最小功能的轻量级引擎。当您需要快速写入许多小表（最多约100万行）并在以后整体读取它们时，该类型的引擎是最有效的。
几种Log表引擎的共性是：

数据被顺序append写到磁盘上；
不支持delete、update；
不支持index；
不支持原子性写；
insert会阻塞select操作。

该类型的引擎：

- TinyLog
- StripeLog
- Log

它们彼此之间的区别是：
- TinyLog：不支持并发读取数据文件，查询性能较差；格式简单，适合用来暂存中间数据；
- StripLog：支持并发读取数据文件，查询性能比TinyLog好；将所有列存储在同一个大文件中，减少了文件个数；
- Log：支持并发读取数据文件，查询性能比TinyLog好；每个列会单独存储在一个独立文件中。


**Integration系列**

该系统表引擎主要用于将外部数据导入到ClickHouse中，或者在ClickHouse中直接操作外部数据源。
- Kafka：将Kafka Topic中的数据直接导入到ClickHouse；
- MySQL：将Mysql作为存储引擎，直接在ClickHouse中对MySQL表进行select等操作；
- JDBC/ODBC：通过指定jdbc、odbc连接串读取数据源；
- HDFS：直接读取HDFS上的特定格式的数据文件。

**Specia系列**

Special系列的表引擎，大多是为了特定场景而定制的。
- Memory：将数据存储在内存中，重启后会导致数据丢失。查询性能极好，适合于对于数据持久性没有要求的1亿一下的小表。在ClickHouse中，通常用来做临时表；
- Buffer：为目标表设置一个内存buffer，当buffer达到了一定条件之后会flush到磁盘；
- ？File：直接将本地文件作为数据存储；
- Null：写入数据被丢弃、读取数据为空。
