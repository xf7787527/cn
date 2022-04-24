# ClickHouse命令行工具连接

本文介绍如何使用ClickHouse命令行工具连接分析型云数据库ClickHouse集群。

## 操作步骤

1. 登录[分析型云数据库 ClickHouse 管理控制台](https://jchdb-console.jdcloud.com)。 

2. 选择需要连接的目标实例 ，您可通过 实例信息 页面，查看外网地址或VPC地址。

3. 根据操作系统类型及云数据库ClickHouse版本下载对应的客户端。下载链接，请参见 [clickhouse-client](https://clickhouse.com/docs/zh/getting-started/install/?spm=a2c4g.11186623.0.0.2156f3daJywCnC#install-from-deb-packages) 。

4. 连接云数据库ClickHouse集群。

   在clickhouse-client客户端的安装目录下执行如下命令。

   ```
   ./clickhouse-client --host=<host> --port=<port> --user=<user> --password=<password>; 
   ```

   参数说明：

   | 参数     | 说明                                                         |
   | -------- | :----------------------------------------------------------- |
   | host     | 外网地址或VPC地址。如果clickhouse-client所在服务器与云数据库ClickHouse集群在同一VPC内，您可以使用VPC地址。否则，请使用外网地址。 |
   | port     | TCP端口号。                                                  |
   | user     | 您通过分析型云数据库ClickHouse控制台创建的数据库账号。       |
   | password | 数据库账号对应的密码。                                       |

   

