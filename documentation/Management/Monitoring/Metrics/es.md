## 云搜索 ElasticSearch

获取该产品监控数据的servicecode为es，提供集群和节点维度维度指标数据。具体如下：

### 集群  

metric | 中文名称  | 英文名称 |单位 | 说明
---|--- |--- |--- |---
jmiss.es.instance.status | 集群状态 | Cluster status | 无 |
jmiss.es.instance.search_qps | 集群查询QPS  | Cluster search qps | Count/s|
jmiss.es.instance.index_qps|集群写入QPS | Cluster indexing qps | Count/s| 　


### 节点
获取某个节点的指标数据时，tags中nodeId 需指定具体的节点ID。 其提供的监控指标如下：  
> 提示：如果您需要获取全部节点（node）的指标数据，可以在调用describeMetricData接口时，把groupBy参数设置为true，tags中的Key指定为nodeId，value值指定为*。详细接口定义，可参考 [describeMetricData接口](https://docs.jdcloud.com/cn/monitoring/api/describemetricdata?content=API)

metric | 中文名称  | 英文名称 |单位 | 说明
---|--- |--- |--- |---
miss.es.node.query_latency| 节点搜索查询延迟 | Node query latency| ms |
jmiss.es.node.index_latency | 节点index延迟 | Node index latency |ms|
jmiss.es.node.fs_used_percent_0_100| 节点磁盘使用率 | Node disk usage | % | 
jmiss.es.node.jvm_heap_used_percent | 节点HeapMemory使用率 | Node heap memory usage | % | 
jmiss.es.container.cpu.util | 节点cpu使用率 | Node os cpu usage | % |
jmiss.es.node.index_active| index线程池active线程数 |Node index thread_pool active threads |count|  
jmiss.es.node.index_queue | index线程池线程队列大小 | Node index thread_pool queue | count|  
jmiss.es.node.index_rejected | index线程池reject任务数 | Node index thread_pool reject | count| 
jmiss.es.node.search_active |search线程池active线程数| Node search thread_pool active threads | count| 
jmiss.es.node.search_queue | search线程池线程队列大小 | Node search thread_pool queue | count| 
jmiss.es.node.search_rejected |search线程池reject任务数 | Node search thread_pool reject | count| 
jmiss.es.node.write_active | write线程池active线程数 | Node write thread_pool active threads | count| 
jmiss.es.node.write_queue| write线程池线程队列大小 |Node write thread_pool | count|  | 
jmiss.es.node.write_rejected |write线程池reject任务数| Node write thread_pool reject | count| 

