## 分析型云数据库ClickHouse

该产品监控数据的servicecode为clickhouse

## 1.metric分组层级信息

主要描述分组之间的层级关系，**groupCode**是一个metric分组的标识，不能重复。

| 分组groupCode（一级） | 分组groupCode（二级，若存在） | 包含的metric | 查询所需tag |
| --------------------- | ----------------------------- | ------------ | ----------- |
| clickHouse-instance   | -                             | -            | 无          |
| clickHouse-node       | -                             | -            | pod         |

## 2，数据库级别 监控指标

| metric                             | 中文名称             | 英文名称                   | 单位 | 说明 |
| ---------------------------------- | -------------------- | -------------------------- | ---- | ---- |
| clickhouse.metric_DiskDataBytes    | 集群总存储空间使用量 | Total Disk Space Usage     | GB   |      |
| clickhouse.metric_DiskDataBytes    | 集群总存储空间剩余量 | Total Disk Space Free      | GB   |      |
| clickhouse.metric_TCPConnection    | 当前TCP活跃连接数    | TCP Connections            | 个   |      |
| clickhouse.metric_HTTPConnection   | 当前HTTP活跃连接数   | HTTP Connections           | 个   |      |
| clickhouse.event_SelectQuery       | QPS                  | Select Queries             | 个/s |      |
| clickhouse.event_InsertedRows      | 插入记录数           | Insert Rows                | 个/s |      |
| clickhouse.event_MergedRows        | 合并记录数           | Merged Rows                | 个/s |      |
| clickhouse.metric_ReplicatedChecks | 复制job数（checks）  | Replication Jobs（checks） | 个   |      |
| clickhouse.metric_ReplicatedFetch  | 复制job数（fetch）   | Replication Jobs（send）   | 个   |      |
| clickhouse.metric_ReplicatedSend   | 复制job数（send）    | Removing Instances         | 个   |      |
| clickhouse.metric_ZooKeeperRequest | ZooKeeper请求数      | Zookeeper Requests         | 个   |      |

## 3，节点级别 监控指标

| metric                                              | 中文名称      | 英文名称                 | 单位 | 说明 |
| --------------------------------------------------- | ------------- | ------------------------ | ---- | ---- |
| clickhouse_pod_cpu_util                             | CPU使用率     | CPU Usage                | %    |      |
| clickhouse_pod_memory_usage                         | 内存使用率    | Memory Usage             | %    |      |
| clickhouse_pod_pv_usage                             | 磁盘使用率    | Disk Usage               | %    |      |
| clickhouse_kubelet_volume_stats_used_bytes          | 磁盘使用量    | Disk Used                | GB   |      |
| clickhouse_volume_bytes_read                        | 磁盘读吞吐量  | Disk Read Throughput     | MBps |      |
| clickhouse_volume_bytes_write                       | 磁盘写吞吐量  | Disk Write Throughput    | MBps |      |
| clickhouse.event_MergedRows                         | 磁盘读取IOPS  | Merged Rows              | 个/s |      |
| clickhouse_volume_io_write                          | 磁盘写入IOPS  | Disk Write IOPS          | 个/s |      |
| clickhouse_container_network_transmit_bytes_total   | 网络出速率    | Network Outbound Rate    | Kbps |      |
| clickhouse_container_network_receive_bytes_total    | 网络进速率    | Network Inbound Rate     | Kbps |      |
| clickhouse_container_network_transmit_packets_total | 网络出包量    | Network Outbound Packets | 个/s |      |
| clickhouse_container_network_receive_packets_total  | 网络进包量    | Network Inbound Packets  | 个/s |      |
| clickhouse_container_spec_cpu_quota                 | CPU配额       | Cpu Quota                |      |      |
| clickhouse_container_cpu_usage_seconds_total        | CPU总使用时间 | Cpu Usage Seconds Total  |      |      |
| clickhouse_container_spec_cpu_period                | CPU Period    | Cpu Period               |      |      |
| clickhouse_container_memory_rss                     | 内存Rss       | Memory Rss               |      |      |
| clickhouse_container_spec_memory_limit_bytes        | 内存Limit     | Memory Limit Bytes       |      |      |