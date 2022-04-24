# 数据导入

本文介绍如何通过clickhouse-client工具将本地文件的数据导入至分析型云数据库ClickHouse。

#### 注意事项

支持导入到云数据库ClickHouse的常见文件格式为TabSeparated、TabSeparatedWithNames、TabSeparatedWithNamesAndTypes、CSV和CSVWithNames。更多支持的文件格式，请参见[文件格式及说明](https://clickhouse.com/docs/zh/interfaces/formats/?spm=a2c4g.11186623.0.0.522ad0d8vz9llf#tabseparated)

#### 前提条件

- 已将云主机的IP地址添加到分析型云数据库ClickHouse的白名单中。

- 已安装与分析型云数据库ClickHouse对应版本的clickhouse-client工具。

  

#### 操作步骤

1. 提前准备好数据文件 account.csv，文件内容如下：

```
accountid, name, address, year
1, 'GHua', 'WuHan Hubei', 1990
2, 'SLiu', 'ShenZhen Guangzhou', 1991
3, 'JPong', 'Chengdu Sichuan', 1992
```

2. 使用 clickhouse-client 连接分析型云数据库ClickHouse实例，创建数据库和表。

   ##### 2.1 连接实例

   1. 实例所在VPC内选择一台云主机，在该云主机内，安装下载客户端 [点击下载clickhouse-client](https://repo.yandex.ru/clickhouse/rpm/stable/x86_64/)。

   2. 安装客户端

   ```
   rpm -ivh *.rpm
   ```

   3. 通过 clickhouse-client客户端 访问该实例

   ​        在clickhouse-client客户端的安装目录下执行如下命令。

   ```
   ./clickhouse-client --host=<host> --port=<port> --user=<user> --password=<password>
   ```

   参数说明：

   | 参数     | 说明                                                         |
   | -------- | :----------------------------------------------------------- |
   | host     | 外网地址或VPC地址。如果clickhouse-client所在服务器与云数据库ClickHouse集群在同一VPC内，您可以使用VPC地址。否则，请使用外网地址。 |
   | port     | TCP端口号。                                                  |
   | user     | 您通过分析型云数据库ClickHouse控制台创建的数据库账号。       |
   | password | 数据库账号对应的密码。                                       |

   

   #####      2.2 创建数据库

   - 高可用模式下创建数据库

   ```
      CREATE DATABASE IF NOT EXISTS testdb ON CLUSTER default;
   ```

   - 非高可用模式下创建数据库   

   ```
      CREATE DATABASE IF NOT EXISTS testdb;
   ```

   ##### 2.3 创建数据表

   - 高可用模式下创建数据表

   ```
   CREATE TABLE testdb.account ON CLUSTER default(accountid UInt16,name String,address String,year UInt64) ENGINE =ReplicatedMergeTree('/clickhouse/tables/{shard}/testdb/account', '{replica}') ORDER BY (accountid);
   ```

   - 非高可用模式下创建数据表

   ```
   CREATE TABLE testdb.account (accountid UInt16, name String, address String, year UInt64) ENGINE =MergeTree() ORDER BY (accountid);
   ```

   

3. 将提前准备好的数据，放到连接分析型云数据库ClickHouse实例的云主机 `/data` 目录下，执行以下命令导入数据。

```
cat <本地文件名> | ./clickhouse-client --host=<数据库连接地址> --port=<TCP端口号> --user=<数据库账号> --password=<数据库账号的密码> --query="INSERT INTO <ClickHouse表名> FORMAT <本地文件格式>";
```

4. 查询数据

```
select * from testdb.account;
```

