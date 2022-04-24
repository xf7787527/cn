# 导入数据

介绍使用clickhouse-client连接到ClickHouse实例以后，如何导入数据。

## 前提条件

已完成快速入门的如下步骤：

[新建实例](https://docs.jdcloud.com/cn/jchdb/create-instance1)

[创建账号](https://docs.jdcloud.com/cn/jchdb/create-account1)

[设置白名单](https://docs.jdcloud.com/cn/jchdb/setwhitelist)

[连接实例](https://docs.jdcloud.com/cn/jchdb/Connect-Instance1)

## 操作步骤

1. 将数据文件导入到 ClickHouse 集群并查看已导入的数据。提前准备好数据文件 account.csv，文件内容如下：

```
accountid, name, address, year
1, 'GHua', 'WuHan Hubei', 1990
2, 'SLiu', 'ShenZhen Guangzhou', 1991
3, 'JPong', 'Chengdu Sichuan', 1992
```

2. 将提前准备好的数据，放到连接 ClickHouse 集群的云服务器 `/data` 目录下，执行以下命令导入数据。

```
cat /data/account.csv | clickhouse-client - hxxx.xxx.xxx.xxx --database=testdb --query="INSERT INTO account FORMAT CSVWithNames"
```

3. 查询数据

```
select * from testdb.account;
```

   

