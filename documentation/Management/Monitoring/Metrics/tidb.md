# 分布式数据库 TiDB

该产品线监控数据的servicecode：tidb ，其提供的监控指标如下：

## TiDB 集群的监控指标

> 备注:
> 1. 每个TiDB连接数  按照不同的tidb 上报，查询时若期望展示每个每个tidb 的连接数，在调用[describeMetricData](https://docs.jdcloud.com/cn/monitoring/api/describemetrics)  接口时把groupBy参数设置为true，tags中的Key指定为kubernetes_pod_name，value值指定为*；或者不传groupBy参数，value值指定为节点的id（节点ID可以通过OpenAPI describeNodes接口获取）；

|metric|中文名称|英文名称|单位|说明|
|:-|:-|:-|:-|:-|
|tidb.type_storage_size.pd_cluster_status|已用存储空间大小|Current storage size|GB||
|tidb.type_storage_capacity.pd_cluster_status|存储空间大小|Current storage capacity|GB||
|tidb.component_tidb.server_connections|每个TiDB连接数|Connection Count|个|参见备注 1|
|tidb.session_transaction_duration_seconds_count|每秒事务执行数量|Transaction OPS|个||
|tidb.type_Insert.executor_statement_total|SQL执行数量(插入)|Statement OPS(insert)|个||
|tidb.type_Delete.executor_statement_total|SQL执行数量(删除)|Statement OPS(delete)|个||
|tidb.type_Update.executor_statement_total|SQL执行数量(更新)|Statement OPS(update)|个||
|tidb.type_Select.executor_statement_total|SQL执行数量(查询)|Statement OPS(select)|个||
|tidb.tidb_executor_statement_total|每秒查询数|QPS|个||

## TiDB 中的节点的监控指标
如果需要获取TiDB 集群中下面各个节点的监控指标，需要传入tags参数。tags的key为pod，value为节点的id。 节点ID可以通过OpenAPI describeNodes接口获取。

|metric|中文名称|英文名称|单位|备注|
|:--|:--|:--|:--|:--|
|tidb_pod_cpu_util|CPU使用率|CPU Usage|%|
|tidb_pod_memory_usage|内存使用率|Memory Usage|%|
|tidb_pod_pv_usage|磁盘使用率|Disk Usage|%|
|tidb_kubelet_volume_stats_used_bytes|磁盘使用量|Disk Used|GB|
|tidb_container_network_transmit_bytes_total|网络出速率|Network Outbound Rate|Kbps|
|tidb_container_network_receive_bytes_total|网络进速率|Network Inbound Rate|Kbps|
|tidb_container_network_transmit_packets_total|网络出包量|Network Outbound Packets|个/s|
|tidb_container_network_receive_packets_total|网络进包量|Network Inbound Packets|个/s|
