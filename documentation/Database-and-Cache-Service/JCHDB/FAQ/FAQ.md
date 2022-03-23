# FAQ

## 选型与购买

#### 1. 购买ClickHouse实例时，推荐选择哪一个版本？

分析型云数据库ClickHouse根据开源社区公开的LTS内核稳定版提供服务，通常在版本推出3个月相对稳定后启动云服务售卖，建议购买20.8及以上版本。

#### 2. ClickHouse实例支持多少个副本？不同副本实例有什么特点

ClickHouse实例支持单个副本和多副本，最多支持到6副本，双副本支持多可用区部署，具体情况可在创建是查看控制台的相关信息。

双副本为高可用HA版，其中当一个副本不可用的情况下， 另一个副本可对外提供服务，建议生产环境使用。

单副本为单机版，副本宕机会影响整个集群，建议测试环境使用。

#### 3.ClickHouse 实例支持多少个分片
ClickHouse实例支持1-128个分片，具体情况可在创建是查看控制台的相关信息。

#### 4. 单个ClickHouse实例支持多少个ZooKeeper节点
单个ClickHouse实例最多可支持9个ZooKeeper节点。

#### 5. ClickHouse实例支持那些地域
ClickHouse实例暂时支持“华北-北京”和“华东-上海”地域，后续视情况支持更多地域。

## 扩容与缩容

#### 1. 垂直扩缩容耗时受什么影响？

升级/降低节点配置会批量重启节点，耗时与集群规格有有关，对2副本及以上的ClickHouse实例基本无影响，建议在业务低峰期进行。

#### 2. 扩磁盘期间对实例有什么影响？

升级存储空间会批量重启节点，建议在业务低峰期进行。

#### 3. 扩缩副本期间对实例有什么影响？

扩缩副本期间，建议集群可读不可写，等待副本调整完成后开启数据写入，请选择在非业务高峰期进行。在数据存储量及查询量均相对增长时，优先选择副本扩容。

## 数据写入与查询

#### 1. 怎么连接某一个具体的节点？

【首先由于特殊的部署方式，直接从select * from system.clusters 查询的host地址ip是无法连接的】

ClickHouse实例的节点默认都是按数字0开始排序，名字有一定规则，相应的节点域名也有一定规则，简单来说可以按下面的sql拼接生成。

登录ClickHouse实例任意一个节点，执行下面sql【xxxxxx 提前替换成ClickHouse实例的GID后半段字符，如 clickhouse-5evgc9ygrw ，只需把xxxxxx替换成 5evgc9ygrw，共三处】

```
select cluster, shard_num,shard_weight, replica_num, concat('chi-ck-xxxxxxxxxxx-',toString(shard_num-1) ,'-', toString(replica_num-1),'-0.chi-ck-xxxxxxxxxxx-' , toString(shard_num-1), '-', toString(replica_num-1),'.ck-xxxxxxxxxxx-hb.jvessel2.jdcloud.com') as host_name, host_address, port, is_local, user, default_database,errors_count, estimated_recovery_time from system.clusters\G
```

#### 2.  磁盘空间爆满，导致数据写入失败怎么办？

查找Part 记录数最多的分区：

```
# 查找分区名
select partition,rows,min_time,max_time from system.parts where table='order_status_vs_shipment_m_shared' order by partition;
 
 
## 查找分区名及大小
select partition,bytes_on_disk,rows,min_time,max_time from system.parts where table='instance_data_local'  and partition like '202106%'  order by rows desc;
 
 
 
##查找并拼接出删除语句
select concat('ALTER TABLE instance_data_local DROP PARTITION ''', partition ,'''') as sql, partition,bytes_on_disk,rows,min_time,max_time from system.parts where table='lineorder'  order by rows desc limit 10;
 
 
##删除分区【建议删本地表，分布式表不支持on cluster语法】
ALTER TABLE instance_data_local DROP PARTITION '20210520';

```

#### 3.  执行ddl异常缓慢，可能某些节点ddl执行失败，问题如何排查？

排查方法：

1. 替换自己的节点id，如 clickhouse-5evgc9ygrw ，只需把xxxxxx替换成 5evgc9ygrw

```
--获取最后一个ddl queue队列
SELECT
    name,
    replaceRegexpAll(replaceRegexpAll(value, '%2D', '-'), '%2E', '.') AS hosts,
    ctime,
    mtime
FROM system.zookeeper
WHERE path = '/clickhouse/ck-xxxxxxxxxx/task_queue/ddl/'
ORDER BY ctime DESC
LIMIT 40
```



根据上图取到的query-xxxxxxxx log id，替换下面sql中的queryID 【注意一起替换XXXXXXXX为你的实例id】, 下图中是执行完的实例id， 没有出现在下列截图中的实例即是有可能出现问题的节点。

```
--根据上面的queue队列获取执行的ddl host
SELECT
    replaceRegexpAll(name, '%2D', '-') AS host,
    ctime,
    mtime,
    path
FROM system.zookeeper
WHERE path = '/clickhouse/ck-xxxxxxxxxx/task_queue/ddl/query-0000000338/finished'
ORDER BY host DESC
LIMIT 40
```



【注意： 并非只可能是最后一个ddl卡住的，但大抵可以根据上述sql找出出问题的节点，找到以后直接连到此分片上，执行show processlist 查看卡住的进程】

#### 4. 如何kill掉一个会话进程？

```
--常规做法：
show processlist ；
 
 
--杀死这个query
KILL QUERY WHERE QUERY_ID = 'XXXXXXXXXXXXXX' ;
 
 
 
--如果以上还不生效，则说明此query可能会引起文件mutation，尝试用下面方法解决：
 
 
--查询会话
SELECT * FROM system.mutations WHERE is_done = 0
 
 
--杀掉这个mutation ， 可能会引起无法修复的后果，数据丢失等等，确认好风险后再执行。
KILL MUTATION WHERE mutation_id = 'xxxxxxxxxxxxx' SYNC
```

