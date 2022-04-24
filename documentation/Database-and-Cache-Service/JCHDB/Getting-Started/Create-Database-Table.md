# 创建数据库和表

使用clickhouse-client连接到ClickHouse实例以后，创建数据库和表。

## 前提条件

已完成快速入门的如下步骤：

[新建实例](https://docs.jdcloud.com/cn/jchdb/create-instance1)

[创建账号](https://docs.jdcloud.com/cn/jchdb/create-account1)

[设置白名单](https://docs.jdcloud.com/cn/jchdb/setwhitelist)

[连接实例](https://docs.jdcloud.com/cn/jchdb/Connect-Instance1)

## 操作步骤

1. 创建数据库

  - 高可用模式下创建数据库

   ```
   CREATE DATABASE IF NOT EXISTS testdb ON CLUSTER default;
   ```

  - 非高可用模式下创建数据库   

   ```
   CREATE DATABASE IF NOT EXISTS testdb ;
   ```

2. 创建数据表

- 高可用模式下创建数据表

```
CREATE TABLE testdb.account ON CLUSTER default(accountid UInt16,name String,address String,year UInt64) ENGINE =ReplicatedMergeTree('/clickhouse/tables/{shard}/testdb/account', '{replica}') ORDER BY (accountid);
```

- 非高可用模式下创建数据表

```
CREATE TABLE testdb.account (accountid UInt16, name String, address String, year UInt64) ENGINE =MergeTree() ORDER BY (accountid);
```











