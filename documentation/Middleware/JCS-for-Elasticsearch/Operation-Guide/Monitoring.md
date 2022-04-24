## 查看监控信息
集群创建成功后，单击集群名称进入集群详情页，可以查看关于集群运行的详细监控信息，辅助集群运维监管。也可由“云监控-资源监控-Elasticsearch监控”进入查看。</br>
### 操作步骤
1.访问[云搜索Elasticsearch控制台](https://es-console.jdcloud.com/clusters)，即进入集群列表页面。</br>

2.在集群列表页面，点击集群名称，进入详情页面。</br>

3.在详情页面，点击【集群监控】进入监控页面。</br>

4.监控时段可选择据当前时间“1小时”、“6小时”、“12小时”进行选择，也可由日历时间段自主选择。</br>

5.单击右上方“设置报警规则”，单击跳转至云监控页面进行报警规则的设置。</br>

![查询1](../../../../image/Internet-Middleware/JCS%20for%20Elasticsearch/监控ES.png)
 
监控指标包括：集群健康状态、集群查询QPS、集群写入QPS、节点CPU使用率、节点磁盘使用率、节点HeapMemory使用率。</br>

### 集群维度
| 指标名称	| metric | 单位 | 说明	|
|:--:|:--:|:--:|:--:| 
| 集群数据节点数 | jmiss.es.instance.data_nodes | count | 当前集群数据节点的数量 | 
| 集群索引数 | jmiss.es.instance.indices | count | 当前集群索引数量 | 
| 集群磁盘使用量 | jmiss.es.instance.fs_used | byte | 当前集群磁盘使用量 | 
| 集群节点数 | jmiss.es.instance.nodes | count | 当前集群节点总数。在变更配置期间，可能会出现增加一倍的情况。 | 
| 集群文档数 | jmiss.es.instance.docs | count | 当前集群文档总数 | 
| 集群分片数 | jmiss.es.instance.active_shards | count | 当前集群分片总数 | 
| 集群迁移中的分片数 | jmiss.es.instance.relocating_shards | count | 当前集群迁移中的分片总数 | 
| 集群主分片数 | jmiss.es.instance.active_primary_shards | count | 当前集群主分片总数 | 
| 集群初始化中的分片数 | jmiss.es.instance.initializing_shards | count | 当前集群初始化中的分片数 | 
| 集群未分配的分片数 | jmiss.es.instance.unassigned_shards | count | 当前集群未分配的分片数 | 
| 集群状态 | jmiss.es.instance.status | 无 | 0 表示绿色；1 表示黄色；2 表示红色， |
| 集群查询QPS | jmiss.es.instance.search_qps | Count/Second | 反应集群查询操作繁忙程度 |
| 集群写入QPS | jmiss.es.instance.index_qps | Count/Second | 反应集群写入操作繁忙程度 |

其中健康状态是云搜索Elasticsearch集群非常重要的监控项，用来表征集群总体上是否工作正常。健康状态种类如下：</br>
|颜色 | 健康状态	|
|:--:|:--: |
| 绿色（green） | 此时集群处于最健康状态，所有的主分片和副本分片都已分配，集群是100%可用的。	|
| 黄色（yellow） | 此时集群的高可用性受到影响，但是搜索结果仍然完整，所有的主分片已经分片了，但至少还有一个副本是缺失的。高可用性在某种程度上被弱化。	|
| 红色（red） | 此时集群异常，搜索只能返回部分数据，至少有一个主分片（以及它的全部副本）都在缺失中。 |

### 节点维度
| 指标名称	| metric | 单位 | 说明	|
|:--:|:--:|:--:|:--:| 
| 节点CPU利用率 | jmiss.es.container.cpu.util | % | CPU 使用率过高会导致集群节点处理能力下降，甚至宕机 |
| 节点磁盘使用率	| jmiss.es.node.fs_used_percent_0_100 | % | 磁盘使用率过高会导致数据无法正常写入 |
| 节点HeapMemory使用率 | jmiss.es.node.jvm_heap_used_percent | % | 数值过高时影响查询性能 | 
| 节点搜索查询延迟 | jmiss.es.node.query_latency | ms | 节点搜索查询请求耗时 | 
| 节点index延迟 | jmiss.es.node.index_latency | ms | 节点 index 请求耗时 | 
| index线程池active线程数 | jmiss.es.node.index_active | count | 单位统计周期（1min）内index线程池active线程数 | 
| index线程池线程队列大小 | jmiss.es.node.index_queue | count | 如果队列大小一直很大，请考虑扩展您的集群 | 
| index线程池reject任务数 | jmiss.es.node.index_rejected | count | 单位统计周期（1min）内index线程池reject任务数 | 
| search线程池active线程数 | jmiss.es.node.search_active | count | 单位统计周期（1min）内search线程池active线程数 | 
| search线程池线程队列大小 | jmiss.es.node.search_queue | count | 如果队列大小一直很大，请考虑扩展您的集群 | 
| search线程池reject任务数 | jmiss.es.node.search_rejected | count | 单位统计周期（1min）内search线程池reject任务数 | 
| write线程池active线程数 | jmiss.es.node.write_active | count | 单位统计周期（1min）内write线程池active线程数 | 
| write线程池线程队列大小 | jmiss.es.node.write_queue | count | 如果队列大小一直很大，请考虑扩展您的集群 | 
| write线程池reject任务数 | jmiss.es.node.write_rejected | count | 单位统计周期（1min）内write线程池reject任务数 | 


