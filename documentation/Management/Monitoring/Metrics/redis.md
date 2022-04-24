#  监控指标说明

#   基础监控组

###   CPU监控

|   监控指标   |  单位   | metric	  |   说明   |   备注  | 
| :--- | :---:  |:---  |:---  |:---  |
| 	实例平均CPU使用率  | 	%	   | jmiss.redis.instance.container.cpu.util  | 单位时间内Redis实例所有Master节点的平均CPU使用率  |通过[describeMetricData](https://docs.jdcloud.com/cn/monitoring/api/describemetricdata)获取监控数据时，aggreType 设置为 avg | 
| 	实例最大CPU使用率   |   %	 |jmiss.redis.instance.container.cpu.util   |   单位时间内Redis实例所有Master节点中最大节点的CPU使用率   | 通过[describeMetricData](https://docs.jdcloud.com/cn/monitoring/api/describemetricdata)获取监控数据时，获取监控数据时，aggreType 设置为 max |   
| 	代理CPU使用率   |   %	   |   jmiss.redis.proxy.container.cpu.util   |   单位时间内单个proxy代理的CPU使用率   |   |
| 	CPU使用率（节点）   |   %	   |   jmiss.redis.instance.container.cpu.util   |   单位时间内单个节点的CPU使用率。可单独查看master节点、slave节点、shard分片维度的情况。   |   |


###  内存监控
|   监控指标   |  单位   | metric	  |   说明   | 
| :--- | :---:  |:---  |:---  |
| 	实例内存使用量   |  Bytes   |  jmiss.redis.cluster.used_memory	   |  单位时间内Redis实例的内存使用量数据   |  
| 	实例内存使用率   |  %	   |  jmiss.redis.cluster.memory_usage	   |  单位时间内Redis实例的内存使用率。为实际使用内存和申请总内存之比   |  
| 	实例节点最大内存使用率   |  %	   |  jmiss.redis.cluster.memory_max_usage	   |  单位时间内Redis实例所有节点中的最大内存使用率   |  
| 	实例Key数量   |  count	   |  jmiss.redis.cluster.db_keys   |  	当前实例的Key数量总计   |  
| 	带过期时间Key数量   |  count	   |  jmiss.redis.cluster.expired_keys	   |  当前实例所有带有过期时间Key的数量   |  
| 	实例驱逐Key数量   |  count	   |  jmiss.redis.cluster.evicted_keys	   |  单位时间内实例驱逐了的Key数量   |  
| 	实例已经过期Key数量   |  count   |  	jmiss.redis.cluster.expires_keys   |  	单位时间内实例上已经过期的Key数量   |  
| 	实例使用内存Rss   |  Bytes	   |  jmiss.redis.cluster.used_memory_rss   |  	单位时间内实例使用内存Rss   |  
| 	代理内存使用率   |  %	   |  jmiss.redis.proxy.memory_usage	   |  proxy代理的内存使用率   |  
| 	内存使用量（节点or 分片）   |  Bytes	   |  jmiss.redis.instance.used_memory   |  	单位时间内的内存使用量数据  |  
| 	内存使用率（节点 or 分片）   |  	%   |  	jmiss.redis.instance.memory_usage	   |  单位时间内的内存使用率。为实际使用内存和申请总内存之比   |  
| 	Key数量（节点or 分片）   |  	count	   |  jmiss.redis.instance.db_keys   |  	当前节点上的Key数量总计   |  
| 	带过期时间Key数量（节点or 分片）	   |  count   |  	jmiss.redis.instance.expired_keys	   |  当前节点上的带有过期时间Key的数量   |  
| 	驱逐Key数量（节点or 分片）	   |  count	   |  jmiss.redis.instance.evicted_keys   |  	当前节点的已被驱逐了的Key数量   |  
| 	已经过期Key数量（节点or 分片）	   |  count	   |  jmiss.redis.instance.expires_keys   |  	当前节点上的已经过期Key的数量   |  
| 	碎片率（节点or 分片）    |   %   |  	jmiss.redis.instance.mem_fragmentation_ratio	   |  当前节点的碎片率   |  
| 	使用内存Rss（节点or 分片）    |   Bytes   |  	jmiss.redis.instance.used_memory_rss	   |  当前节点上的使用内存Rss   |  
| 	内存消耗峰值（节点or 分片）   |    Bytes   |  	jmiss.redis.instance.used_memory_peak	   |  当前节点上的内存消耗峰值   |  


###  网络监控
|   监控指标   |  单位   | metric	  |   说明   | 
| :--- | :---:  |:---  |:---  |
| 	客户端到代理的TCP连接数 | 	count	| 	jmiss.redis.cluster.connected_clients	| 	单位时间内客户端到Proxy代理的TCP连接数总和| 	
| 	实例连接使用率| 	%	| 	jmiss.redis.cluster.conn_usage| 		实际 TCP 连接数量和最大连接数比| 	
| 	实例内网进流量| 	KBps| 		jmiss.redis.cluster.net_io_in_per_sec	| 	内网进入流量| 	
| 	实例内网出流量| 	KBps| 		jmiss.redis.cluster.net_io_out_per_sec	| 	内网出口流量| 	
| 	实例最大执行时延| 	ms| 		jmiss.redis.cluster.max_delay| 		Proxy 到 Redis Server 的执行时延最大值| 	
| 	代理当前连接数| 	count| 		jmiss.redis.proxy.connected_clients	| 	单位时间内Proxy代理的连接数总和| 	
| 	代理连接使用率| 	%	| 	jmiss.redis.proxy.connection_usage	| 	Proxy上的实际 TCP 连接数量和最大连接数比| 	
| 	代理入口带宽| 	Bps	| 	jmiss.redis.proxy.net_in	| 	Proxy上的入口带宽| 	
| 	代理出口带宽  | 	Bps	| 	jmiss.redis.proxy.net_out	 | 	Proxy上的出口带宽| 	
| 	代理最大时延 | 	ms  | 		jmiss.redis.proxy.max_latency	| 	单位时间内Proxy的执行时延最大值| 	
| 	TCP连接数 （节点）| 	count	| 	jmiss.redis.instance.connected_clients	| 	单位时间内与Redis的连接数| 	
| 	最大执行时延（节点）| 	ms	| 	jmiss.redis.instance.max_latency	Redis | 	节点最大延迟| 	
| 	内网进流量（节点）| 	KBps	| 	jmiss.redis.instance.net_io_in_per_sec	| 	内网进入流量| 	
| 	内网出流量（节点）| 	KBps	| 	jmiss.redis.instance.net_io_out_per_sec	| 	内网出口流量| 	


###  请求监控
|   监控指标   |  单位   | metric	  |   说明   | 
| :--- | :---:  |:---  |:---  |
| 	实例OPS  | 	count/s	| 	jmiss.redis.cluster.instantaneous_ops_per_sec	| 	单位时间内实例的OPS 总和| 	
| 	实例协议错误次数   | 	count/s	| 	jmiss.redis.cluster.protocol_errors	| 	单位时间内实例协议的错误次数 | 	
| 	代理OPS   | 	count/s	| 	jmiss.redis.proxy.ops	| 	单位时间内Proxy的OPS 总和 | 	
| 	代理协议错误次数  | 	count/s	| 	jmiss.redis.proxy.protocol_errors	| 	单位时间内Proxy协议的错误次数| 	
| 	OPS （节点）| 	count/s	 | 	jmiss.redis.instance.instantaneous_ops_per_sec	| 	单位时间内某个节点的的OPS 总和| 	


###  响应监控
|   监控指标   |  单位   | metric	  |   说明   | 
| :--- | :---:  |:---  |:---  |
| 	实例慢查询次数  | 	count/s| 		jmiss.redis.cluster.slowlog_times	| 	单位时间内实例的慢查询次数| 	
| 	实例命中次数  | 	count  | 		jmiss.redis.cluster.keyspace_hits	| 	每秒key的命中数量| 	
| 	实例未命中次数 | 	count	| 	jmiss.redis.cluster.keyspace_misses	| 	每秒key的未命中数量| 	
| 	实例命中率 | 	%	| 	jmiss.redis.cluster.keyspace_hit_rate	| 	实例命中次数 ÷（实例命中次数+实例未命中次数） | 	
| 	慢查询次数（节点） | 	count/s | 		jmiss.redis.instance.slowlog_times	| 	单位时间内当前节点的慢查询次数| 	
| 	命中次数（节点） | 	count	| 	jmiss.redis.instance.keyspace_hits	| 	每秒key的命中数量| 	
| 	未命中次数（节点）| 	count	| 	jmiss.redis.instance.keyspace_misses	| 	每秒key的未命中数量| 	
| 	命中率（节点）| 	%	| 	jmiss.redis.instance.keyspace_hit_rate	| 	节点命中次数 ÷（节点命中次数+节点未命中次数） | 	


### 异常监控
| 监控指标 | 单位 | metric | 说明 |
| :--- | :---: |:--- |:--- |
|  主节点故障  | count  |   jmiss.redis.cluster.master_in_failover  | 单位时间内实例的所有主节点发生故障的次数    |
|  从节点故障  | count  |  jmiss.redis.cluster.replica_in_failover  | 单位时间内实例的所有从节点发生故障的次数    |
|  Proxy 节点故障  | count  |  jmiss.redis.cluster.proxy_in_failover  | 单位时间内实例的所有proxy节点发生故障的次数    |




# 命令统计类监控组

## 实例
提供String监控、Keys监控、Hashes监控、List监控、Sets监控、Zset监控。各个监控组对应的指标如下：



### Keys监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.cluster.del_used_times|实例del命令使用次数|Instance del Command Used Times|count|
jmiss.redis.cluster.dump_used_times|实例dump命令使用次数|Instance dump Command Used Times|count|
jmiss.redis.cluster.exists_used_times|实例exists命令使用次数|Instance exists Command Used Times|count/s|
jmiss.redis.cluster.expire_used_times|实例expire命令使用次数|Instance expire Command Used Times|count/s|
jmiss.redis.cluster.expireat_used_times|实例expireat命令使用次数|Instance expireat Command Used Times|count/s|
jmiss.redis.cluster.keys_used_times|实例keys命令使用次数|Instance keys Command Used Times|count/s|
jmiss.redis.cluster.persist_used_times|实例persist命令使用次数|Instance persist Command Used Times|count/s|
jmiss.redis.cluster.pexpire_used_times|实例pexpire命令使用次数|Instance pexpire Command Used Times|count/s|
jmiss.redis.cluster.pexpireat_used_times|实例pexpireat命令使用次数|Instance pexpireat Command Used Times|count/s|
jmiss.redis.cluster.pttl_used_times|实例pttl命令使用次数|Instance pttl Command Used Times|count/s|
jmiss.redis.cluster.restore_used_times|实例restore命令使用次数|Instance restore Command Used Times|count/s|
jmiss.redis.cluster.sort_used_times|实例sort命令使用次数|Instance sort Command Used Times|count/s|
jmiss.redis.cluster.ttl_used_times|实例ttl命令使用次数|Instance ttl Command Used Times|count/s|
jmiss.redis.cluster.type_used_times|实例type命令使用次数|Instance type Command Used Times|count/s|
jmiss.redis.cluster.scan_used_times|实例scan命令使用次数|Instance scan Command Used Times|count/s|
jmiss.redis.cluster.del_avg_rt|实例del命令平均响应时间|Instance del Command Average Response Time|us|
jmiss.redis.cluster.dump_avg_rt|实例dump命令平均响应时间|Instance dump Command Average Response Time|us|
jmiss.redis.cluster.exists_avg_rt|实例exists命令平均响应时间|Instance exists Command Average Response Time|us|
jmiss.redis.cluster.expire_avg_rt|实例expire命令平均响应时间|Instance expire Command Average Response Time|us|
jmiss.redis.cluster.expireat_avg_rt|实例expireat命令平均响应时间|Instance expireat Command Average Response Time|us|
jmiss.redis.cluster.keys_avg_rt|实例keys命令平均响应时间|Instance keys Command Average Response Time|us|
jmiss.redis.cluster.persist_avg_rt|实例persist命令平均响应时间|Instance persist Command Average Response Time|us|
jmiss.redis.cluster.pexpire_avg_rt|实例pexpire命令平均响应时间|Instance pexpire Command Average Response Time|us|
jmiss.redis.cluster.pexpireat_avg_rt|实例pexpireat命令平均响应时间|Instance pexpireat Command Average Response Time|us|
jmiss.redis.cluster.pttl_avg_rt|实例pttl命令平均响应时间|Instance pttl Command Average Response Time|us|
jmiss.redis.cluster.restore_avg_rt|实例restore命令平均响应时间|Instance restore Command Average Response Time|us|
jmiss.redis.cluster.sort_avg_rt|实例sort命令平均响应时间|Instance sort Command Average Response Time|us|
jmiss.redis.cluster.ttl_avg_rt|实例ttl命令平均响应时间|Instance ttl Command Average Response Time|us|
jmiss.redis.cluster.type_avg_rt|实例type命令平均响应时间|Instance type Command Average Response Time|us|
jmiss.redis.cluster.scan_avg_rt|实例scan命令使用次数|Instance scan Command Used Times|us|
jmiss.redis.cluster.touch_used_times|实例touch命令使用次数|Instance touch Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.cluster.unlink_used_times|实例unlink命令使用次数|Instance unlink Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.cluster.move_used_times|实例move命令使用次数|Instance move Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.cluster.randomkey_used_times|实例randomkey命令使用次数 |Instance randomkey Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.cluster.touch_avg_rt|实例touch命令平均响应时间|Instance touch Command Average Response Time|us|仅redis4.0 有该指标|
miss.redis.cluster.unlink_avg_rt|实例unlink命令平均响应时间|Instance unlink Command Average Response Time|us|仅redis4.0 有该指标|
jmiss.redis.cluster.move_avg_rt|实例move命令平均响应时间|Instance move Command Average Response Time|us|仅redis4.0 有该指标|
jmiss.redis.cluster.randomkey_avg_rt|实例randomkey命令平均响应时间|Instance randomkey Command Average Response Time|us|仅redis4.0 有该指标|


### String监控组
metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.cluster.append_avg_rt|实例append命令平均响应时间|Instance append Command Average Response Time|us|
jmiss.redis.cluster.bitcount_avg_rt|实例bitcount命令平均响应时间|Instance bitcount Command Average Response Time|us|
jmiss.redis.cluster.bitpos_avg_rt|实例bitpos命令平均响应时间|Instance bitpos Command Average Response Time|us|
jmiss.redis.cluster.decr_avg_rt|实例decr命令平均响应时间|Instance decr Command Average Response Time|us|
jmiss.redis.cluster.decrby_avg_rt|实例decrby命令平均响应时间|Instance decrby Command Average Response Time|us
jmiss.redis.cluster.get_avg_rt|实例get命令平均响应时间|Instance get Command Average Response Time|us|
jmiss.redis.cluster.getbit_avg_rt|实例getbit命令平均响应时间|Instance getbit Command Average Response Time|us|
jmiss.redis.cluster.getrange_avg_rt|实例getrange命令平均响应时间|Instance getrange Command Average Response Time|us|
jmiss.redis.cluster.getset_avg_rt|实例getset命令平均响应时间|Instance getset Command Average Response Time|us|
jmiss.redis.cluster.incr_avg_rt|实例incr命令平均响应时间|Instance incr Command Average Response Time|us|
jmiss.redis.cluster.incrby_avg_rt|实例incrby命令平均响应时间|Instance incrby Command Average Response Time|us|
jmiss.redis.cluster.incrbyfloat_avg_rt|实例incrbyfloat命令平均响应时间|Instance incrbyfloat Command Average Response Time|us|
jmiss.redis.cluster.mget_avg_rt|实例mget命令平均响应时间|Instance mget Command Average Response Time|us|
jmiss.redis.cluster.mset_avg_rt|实例mset命令平均响应时间|Instance mset Command Average Response Time|us|
jmiss.redis.cluster.psetex_avg_rt|实例psetex命令平均响应时间|Instance psetex Command Average Response Time|us|
jmiss.redis.cluster.set_avg_rt|实例set命令平均响应时间|Instance set Command Average Response Time|us|
jmiss.redis.cluster.setbit_avg_rt|实例setbit命令平均响应时间|Instance setbit Command Average Response Time|us|
jmiss.redis.cluster.setex_avg_rt|实例setex命令平均响应时间|Instance setex Command Average Response Time|us|
jmiss.redis.cluster.setnx_avg_rt|实例setnx命令平均响应时间|Instance setnx Command Average Response Time|us|
jmiss.redis.cluster.setrange_avg_rt|实例setrange命令平均响应时间|Instance setrange Command Average Response Time|us|
jmiss.redis.cluster.strlen_avg_rt|实例strlen命令平均响应时间|Instance strlen Command Average Response Time|us|
jmiss.redis.cluster.append_used_times|实例append命令使用次数|Instance append Command Used Times|count/s|
jmiss.redis.cluster.bitcount_used_times|实例bitcount命令使用次数|Instance bitcount Command Used Times|count/s|
jmiss.redis.cluster.bitpos_used_times|实例bitpos命令使用次数|Instance bitpos Command Used Times|count/s|
jmiss.redis.cluster.decr_used_times|实例decr命令使用次数|Instance decr Command Used Times|count/s|
jmiss.redis.cluster.decrby_used_times|实例decrby命令使用次数|Instance decrby Command Average Response Time|us|
jmiss.redis.cluster.get_used_times|实例get命令使用次数|Instance get Command Used Times|count/s|
jmiss.redis.cluster.getbit_used_times|实例getbit命令使用次数|Instance getbit Command Used Times|count/s|
jmiss.redis.cluster.getrange_used_times|实例getrange命令使用次数|Instance getrange Command Used Times|count/s|
jmiss.redis.cluster.getset_used_times|实例getset命令使用次数|Instance getset Command Used Times|count/s|
jmiss.redis.cluster.incr_used_times|实例incr命令使用次数|Instance incr Command Used Times|count/s|
jmiss.redis.cluster.incrby_used_times|实例incrby命令使用次数|Instance incrby Command Used Times|count/s|
jmiss.redis.cluster.incrbyfloat_used_times|实例incrbyfloat命令使用次数|Instance incrbyfloat Command Used Times|count/s|
jmiss.redis.cluster.mget_used_times|实例incrbyfloat命令使用次数|Instance incrbyfloat Command Used Times|count/s|
jmiss.redis.cluster.mset_used_times|实例mget命令使用次数|Instance mget Command Used Times|count/s|
jmiss.redis.cluster.psetex_used_times|实例psetex命令使用次数|Instance psetex Command Used Times|count/s|
jmiss.redis.cluster.set_used_times|实例set命令使用次数|Instance set Command Used Times|count/s|
jmiss.redis.cluster.setbit_used_times|实例setbit命令使用次数|Instance setbit Command Used Times|count/s|
jmiss.redis.cluster.setex_used_times|实例setex命令使用次数|Instance setex Command Used Times|count/s|
jmiss.redis.cluster.setnx_used_times|实例setnx命令使用次数|Instance setnx Command Used Times|count/s|
jmiss.redis.cluster.setrange_used_times|实例setrange命令使用次数|Instance setrange Command Used Times|count/s|
jmiss.redis.cluster.strlen_used_times|实例strlen命令使用次数|Instance strlen Command Used Times|count/s|

### Hashes监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.cluster.hdel_used_times|实例hdel命令使用次数|Instance hdel Command Used Times|count/s|
jmiss.redis.cluster.hexists_used_times|实例hexists命令使用次数|Instance hexists Command Used Times|count/s|
jmiss.redis.cluster.hget_used_times|实例hget命令使用次数|Instance hget Command Used Times|count/s|
jmiss.redis.cluster.hgetall_used_times|实例hgetall命令使用次数|Instance hgetall Command Used Times|count/s|
jmiss.redis.cluster.hincrby_used_times|实例hincrby命令使用次数|Instance hincrby Command Used Times|count/s|
jmiss.redis.cluster.hincrbyfloat_used_times|实例hincrbyfloat命令使用次数|Instance hincrbyfloat Command Used Times|count/s|
jmiss.redis.cluster.hkeys_used_times|实例hkeys命令使用次数|Instance hkeys Command Used Times|count/s|
jmiss.redis.cluster.hlen_used_times|实例hlen命令使用次数|Instance hlen Command Used Times|count/s|
jmiss.redis.cluster.hmget_used_times|实例hmget命令使用次数|Instance hmget Command Used Times|count/s|
jmiss.redis.cluster.hmset_used_times|实例hmset命令使用次数|Instance hmset Command Used Times|count/s|
jmiss.redis.cluster.hset_used_times|实例hset命令使用次数|Instance hset Command Used Times|count/s|
jmiss.redis.cluster.hsetnx_used_times|实例hsetnx命令使用次数|Instance hsetnx Command Used Times|count/s|
jmiss.redis.cluster.hvals_used_times|实例hvals命令使用次数|Instance hvals Command Used Times|count/s|
jmiss.redis.cluster.hscan_used_times|实例hscan命令使用次数|Instance hscan Command Used Times|count/s|
jmiss.redis.cluster.hdel_avg_rt |实例hdel命令平均响应时间|Instance hdel Command Average Response Time|us|
jmiss.redis.cluster.hexists_avg_rt |实例hexists命令平均响应时间|Instance hexists Command Average Response Time | count/s
jmiss.redis.cluster.hget_avg_rt|实例hget命令平均响应时间|Instance hget Command Average Response Time|count/s|
jmiss.redis.cluster.hgetall_avg_rt|实例hgetall命令平均响应时间|Instance hgetall Command Average Response Time|us|
jmiss.redis.cluster.hincrby_avg_rt|实例hincrby命令平均响应时间|Instance hincrby Command Average Response Time|us|
jmiss.redis.cluster.hincrbyfloat_avg_rt|实例hincrbyfloat命令平均响应时间|Instance hincrbyfloat Command Average Response Time|us|
jmiss.redis.cluster.hkeys_avg_rt|实例hkeys命令平均响应时间| Instance hkeys Command Average Response Time |us|
jmiss.redis.cluster.hlen_avg_rt|实例hlen命令平均响应时间|Instance hlen Command Average Response Time|us|
jmiss.redis.cluster.hmget_avg_rt|实例hmget命令平均响应时间|Instance hmget Command Average Response Time|us|
jmiss.redis.cluster.hmset_avg_rt|实例hmset命令平均响应时间|Instance hmset Command Average Response Time|us|
jmiss.redis.cluster.hset_avg_rt|实例hset命令平均响应时间|Instance hset Command Average Response Time|us|
jmiss.redis.cluster.hsetnx_avg_rt|实例hsetnx命令平均响应时间|Instance hsetnx Command Average Response Time|us|
jmiss.redis.cluster.hvals_avg_rt|实例hvals命令平均响应时间|Instance hvals Command Average Response Time|us|
jmiss.redis.cluster.hscan_avg_rt|实例hscan命令平均响应时间|Instance hscan Command Average Response Time|us|
jmiss.redis.cluster.hstrlen_used_times|实例hstrlen命令使用次数|Instance hstrlen Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.cluster.hstrlen_avg_rt|实例hstrlen命令平均响应时间|Instance hstrlen Command Average Response Time|us|仅redis4.0 有该指标|


### Lists监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.cluster.lindex_used_times|实例lindex命令使用次数|Instance lindex Command Used Times|count/s
jmiss.redis.cluster.linsert_used_times|实例linsert命令使用次数|Instance linsert Command Used Times|count/s|
jmiss.redis.cluster.llen_used_times|实例llen命令使用次数|Instance llen Command Used Times|count/s|
jmiss.redis.cluster.lpop_used_times|实例lpop命令使用次数|Instance lpop Command Used Times|count/s|
jmiss.redis.cluster.lpush_used_times|实例lpush命令使用次数|Instance lpush Command Used Times|count/s|
jmiss.redis.cluster.lpushx_used_times|实例lpushx命令使用次数|Instance lpushx Command Used Times|count/s|
jmiss.redis.cluster.lrange_used_times|实例lrange命令使用次数|Instance lrange Command Used Times|count/s|
jmiss.redis.cluster.lrem_used_times|实例lrem命令使用次数|Instance lrem Command Used Times|count/s|
jmiss.redis.cluster.lset_used_times|实例lset命令使用次数|Instance lset Command Used Times|count/s|
jmiss.redis.cluster.ltrim_used_times|实例ltrim命令使用次数|Instance ltrim Command Used Times|count/s|
jmiss.redis.cluster.rpop_used_times|实例rpop命令使用次数|Instance rpop Command Used Times|count/s|
jmiss.redis.cluster.rpush_used_times|实例rpush命令使用次数|Instance rpush Command Used Times|count/s|
jmiss.redis.cluster.rpushx_used_times|实例rpushx命令使用次数|Instance rpushx Command Used Times|count/s|
jmiss.redis.cluster.lindex_avg_rt|实例lindex命令平均响应时间|Instance lindex Command Average Response Time|us|
jmiss.redis.cluster.linsert_avg_rt|实例linsert命令平均响应时间|Instance linsert Command Average Response Time|us|
jmiss.redis.cluster.llen_avg_rt|实例llen命令平均响应时间|Instance llen Command Average Response Time|us|
jmiss.redis.cluster.lpop_avg_rt|实例lpop命令平均响应时间|Instance lpop Command Average Response Time|us|
jmiss.redis.cluster.lpush_avg_rt|实例lpush命令平均响应时间|Instance lpush Command Average Response Time|us|
jmiss.redis.cluster.lpushx_avg_rt|实例lpushx命令平均响应时间|Instance lpushx Command Average Response Time|us|
jmiss.redis.cluster.lrange_avg_rt|实例lrange命令平均响应时间|Instance lrange Command Average Response Time|us|
jmiss.redis.cluster.lrem_avg_rt|实例lrem命令平均响应时间|Instance lrem Command Average Response Time|us|
jmiss.redis.cluster.lset_avg_rt|实例lset命令平均响应时间|Instance lset Command Average Response Time|us|
jmiss.redis.cluster.ltrim_avg_rt|实例ltrim命令平均响应时间|Instance ltrim Command Average Response Time|us|
jmiss.redis.cluster.rpop_avg_rt|实例rpop命令平均响应时间|Instance rpop Command Average Response Time|us|
jmiss.redis.cluster.rpush_avg_rt|实例rpush命令平均响应时间|Instance rpush Command Average Response Time|us|
jmiss.redis.cluster.rpushx_avg_rt|实例rpushx命令平均响应时间|Instance rpushx Command Average Response Time|us|

### Sets监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.cluster.sadd_used_times|实例sadd命令使用次数|Instance  sadd Command Used Times|count/s| 
jmiss.redis.cluster.scard_used_times| 实例scard命令使用次数 |Instance  scard Command Used Times|count/s| 
jmiss.redis.cluster.sismember_used_times|实例sismember命令使用次数|Instance  sismember Command Used Times|count/s|
jmiss.redis.cluster.smembers_used_times|实例smembers命令使用次数|Instance  smembers Command Used Times|count/s|
jmiss.redis.cluster.spop_used_times|实例spop命令使用次数|Instance  spop Command Used Times|count/s|
jmiss.redis.cluster.srandmember_used_times|实例srandmember命令使用次数|Instance  srandmember Command Used Times|count/s|
jmiss.redis.cluster.srem_used_times|实例srem命令使用次数|Instance  srem Command Used Times|count/s|
jmiss.redis.cluster.sscan_used_times|实例sscan命令使用次数|Instance  sscan Command Used Times | count/s|
jmiss.redis.cluster.sadd_avg_rt|实例sadd命令平均响应时间|Instance  sadd Command Average Response Time|us| 
jmiss.redis.cluster.scard_avg_rt|实例scard命令平均响应时间|Instance  scard Command Average Response Time|us|
jmiss.redis.cluster.sismember_avg_rt|实例sismember命令平均响应时间|Instance  sismember Command Average Response Time|us|
jmiss.redis.cluster.smembers_avg_rt|实例smembers命令平均响应时间|Instance  smembers Command Average Response Time|us|
jmiss.redis.cluster.spop_avg_rt|实例spop命令平均响应时间|Instance  spop Command Average Response Time|us|
jmiss.redis.cluster.srandmember_avg_rt|实例srandmember命令平均响应时间|Instance  srandmember Command Average Response Time|us|
jmiss.redis.cluster.srem_avg_rt|实例srem命令平均响应时间|Instance  srem Command Average Response Time|us|
jmiss.redis.cluster.sscan_avg_rt|实例sscan命令平均响应时间|Instance  sscan Command Average Response Time|us|



## 分片
若获取分片的监控指标数据时，tags中的shardId需指定需查询的分片ID。



### Keys监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.instance.del_used_times|分片del命令使用次数|Instance del Command Used Times|count|
jmiss.redis.instance.dump_used_times|分片dump命令使用次数|Instance dump Command Used Times|count|
jmiss.redis.instance.exists_used_times|分片exists命令使用次数|Instance exists Command Used Times|count/s|
jmiss.redis.instance.expire_used_times|分片expire命令使用次数|Instance expire Command Used Times|count/s|
jmiss.redis.instance.expireat_used_times|分片expireat命令使用次数|Instance expireat Command Used Times|count/s|
jmiss.redis.instance.keys_used_times|分片keys命令使用次数|Instance keys Command Used Times|count/s|
jmiss.redis.instance.persist_used_times|分片persist命令使用次数|Instance persist Command Used Times|count/s|
jmiss.redis.instance.pexpire_used_times|分片pexpire命令使用次数|Instance pexpire Command Used Times|count/s|
jmiss.redis.instance.pexpireat_used_times|分片pexpireat命令使用次数|Instance pexpireat Command Used Times|count/s|
jmiss.redis.instance.pttl_used_times|分片pttl命令使用次数|Instance pttl Command Used Times|count/s|
jmiss.redis.instance.restore_used_times|分片restore命令使用次数|Instance restore Command Used Times|count/s|
jmiss.redis.instance.sort_used_times|分片sort命令使用次数|Instance sort Command Used Times|count/s|
jmiss.redis.instance.ttl_used_times|分片ttl命令使用次数|Instance ttl Command Used Times|count/s|
jmiss.redis.instance.type_used_times|分片type命令使用次数|Instance type Command Used Times|count/s|
jmiss.redis.instance.scan_used_times|分片scan命令使用次数|Instance scan Command Used Times|count/s|
jmiss.redis.instance.del_avg_rt|分片del命令平均响应时间|Instance del Command Average Response Time|us|
jmiss.redis.instance.dump_avg_rt|分片dump命令平均响应时间|Instance dump Command Average Response Time|us|
jmiss.redis.instance.exists_avg_rt|分片exists命令平均响应时间|Instance exists Command Average Response Time|us|
jmiss.redis.instance.expire_avg_rt|分片expire命令平均响应时间|Instance expire Command Average Response Time|us|
jmiss.redis.instance.expireat_avg_rt|分片expireat命令平均响应时间|Instance expireat Command Average Response Time|us|
jmiss.redis.instance.keys_avg_rt|分片keys命令平均响应时间|Instance keys Command Average Response Time|us|
jmiss.redis.instance.persist_avg_rt|分片persist命令平均响应时间|Instance persist Command Average Response Time|us|
jmiss.redis.instance.pexpire_avg_rt|分片pexpire命令平均响应时间|Instance pexpire Command Average Response Time|us|
jmiss.redis.instance.pexpireat_avg_rt|分片pexpireat命令平均响应时间|Instance pexpireat Command Average Response Time|us|
jmiss.redis.instance.pttl_avg_rt|分片pttl命令平均响应时间|Instance pttl Command Average Response Time|us|
jmiss.redis.instance.restore_avg_rt|分片restore命令平均响应时间|Instance restore Command Average Response Time|us|
jmiss.redis.instance.sort_avg_rt|分片sort命令平均响应时间|Instance sort Command Average Response Time|us|
jmiss.redis.instance.ttl_avg_rt|分片ttl命令平均响应时间|Instance ttl Command Average Response Time|us|
jmiss.redis.instance.type_avg_rt|分片type命令平均响应时间|Instance type Command Average Response Time|us|
jmiss.redis.instance.scan_avg_rt|分片scan命令使用次数|Instance scan Command Used Times|us|
jmiss.redis.instance.touch_used_times|分片touch命令使用次数|Instance touch Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.instance.unlink_used_times|分片unlink命令使用次数|Instance unlink Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.instance.move_used_times|分片move命令使用次数|Instance move Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.instance.randomkey_used_times|分片randomkey命令使用次数 |Instance randomkey Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.instance.touch_avg_rt|分片touch命令平均响应时间|Instance touch Command Average Response Time|us|仅redis4.0 有该指标|
miss.redis.instance.unlink_avg_rt|分片unlink命令平均响应时间|Instance unlink Command Average Response Time|us|仅redis4.0 有该指标|
jmiss.redis.instance.move_avg_rt|分片move命令平均响应时间|Instance move Command Average Response Time|us|仅redis4.0 有该指标|
jmiss.redis.instance.randomkey_avg_rt|分片randomkey命令平均响应时间|Instance randomkey Command Average Response Time|us|仅redis4.0 有该指标|

### String监控组
metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.instance.append_avg_rt|分片append命令平均响应时间|Instance append Command Average Response Time|us|
jmiss.redis.instance.bitcount_avg_rt|分片bitcount命令平均响应时间|Instance bitcount Command Average Response Time|us|
jmiss.redis.instance.bitpos_avg_rt|分片bitpos命令平均响应时间|Instance bitpos Command Average Response Time|us|
jmiss.redis.instance.decr_avg_rt|分片decr命令平均响应时间|Instance decr Command Average Response Time|us|
jmiss.redis.instance.decrby_avg_rt|分片decrby命令平均响应时间|Instance decrby Command Average Response Time|us
jmiss.redis.instance.get_avg_rt|分片get命令平均响应时间|Instance get Command Average Response Time|us|
jmiss.redis.instance.getbit_avg_rt|分片getbit命令平均响应时间|Instance getbit Command Average Response Time|us|
jmiss.redis.instance.getrange_avg_rt|分片getrange命令平均响应时间|Instance getrange Command Average Response Time|us|
jmiss.redis.instance.getset_avg_rt|分片getset命令平均响应时间|Instance getset Command Average Response Time|us|
jmiss.redis.instance.incr_avg_rt|分片incr命令平均响应时间|Instance incr Command Average Response Time|us|
jmiss.redis.instance.incrby_avg_rt|分片incrby命令平均响应时间|Instance incrby Command Average Response Time|us|
jmiss.redis.instance.incrbyfloat_avg_rt|分片incrbyfloat命令平均响应时间|Instance incrbyfloat Command Average Response Time|us|
jmiss.redis.instance.mget_avg_rt|分片mget命令平均响应时间|Instance mget Command Average Response Time|us|
jmiss.redis.instance.mset_avg_rt|分片mset命令平均响应时间|Instance mset Command Average Response Time|us|
jmiss.redis.instance.psetex_avg_rt|分片psetex命令平均响应时间|Instance psetex Command Average Response Time|us|
jmiss.redis.instance.set_avg_rt|分片set命令平均响应时间|Instance set Command Average Response Time|us|
jmiss.redis.instance.setbit_avg_rt|分片setbit命令平均响应时间|Instance setbit Command Average Response Time|us|
jmiss.redis.instance.setex_avg_rt|分片setex命令平均响应时间|Instance setex Command Average Response Time|us|
jmiss.redis.instance.setnx_avg_rt|分片setnx命令平均响应时间|Instance setnx Command Average Response Time|us|
jmiss.redis.instance.setrange_avg_rt|分片setrange命令平均响应时间|Instance setrange Command Average Response Time|us|
jmiss.redis.instance.strlen_avg_rt|分片strlen命令平均响应时间|Instance strlen Command Average Response Time|us|
jmiss.redis.instance.append_used_times|分片append命令使用次数|Instance append Command Used Times|count/s|
jmiss.redis.instance.bitcount_used_times|分片bitcount命令使用次数|Instance bitcount Command Used Times|count/s|
jmiss.redis.instance.bitpos_used_times|分片bitpos命令使用次数|Instance bitpos Command Used Times|count/s|
jmiss.redis.instance.decr_used_times|分片decr命令使用次数|Instance decr Command Used Times|count/s|
jmiss.redis.instance.decrby_used_times|分片decrby命令使用次数|Instance decrby Command Average Response Time|us|
jmiss.redis.instance.get_used_times|分片get命令使用次数|Instance get Command Used Times|count/s|
jmiss.redis.instance.getbit_used_times|分片getbit命令使用次数|Instance getbit Command Used Times|count/s|
jmiss.redis.instance.getrange_used_times|分片getrange命令使用次数|Instance getrange Command Used Times|count/s|
jmiss.redis.instance.getset_used_times|分片getset命令使用次数|Instance getset Command Used Times|count/s|
jmiss.redis.instance.incr_used_times|分片incr命令使用次数|Instance incr Command Used Times|count/s|
jmiss.redis.instance.incrby_used_times|分片incrby命令使用次数|Instance incrby Command Used Times|count/s|
jmiss.redis.instance.incrbyfloat_used_times|分片incrbyfloat命令使用次数|Instance incrbyfloat Command Used Times|count/s|
jmiss.redis.instance.mget_used_times|分片incrbyfloat命令使用次数|Instance incrbyfloat Command Used Times|count/s|
jmiss.redis.instance.mset_used_times|分片mget命令使用次数|Instance mget Command Used Times|count/s|
jmiss.redis.instance.psetex_used_times|分片psetex命令使用次数|Instance psetex Command Used Times|count/s|
jmiss.redis.instance.set_used_times|分片set命令使用次数|Instance set Command Used Times|count/s|
jmiss.redis.instance.setbit_used_times|分片setbit命令使用次数|Instance setbit Command Used Times|count/s|
jmiss.redis.instance.setex_used_times|分片setex命令使用次数|Instance setex Command Used Times|count/s|
jmiss.redis.instance.setnx_used_times|分片setnx命令使用次数|Instance setnx Command Used Times|count/s|
jmiss.redis.instance.setrange_used_times|分片setrange命令使用次数|Instance setrange Command Used Times|count/s|
jmiss.redis.instance.strlen_used_times|分片strlen命令使用次数|Instance strlen Command Used Times|count/s|

### Hashes监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.instance.hdel_used_times|分片hdel命令使用次数|Instance hdel Command Used Times|count/s|
jmiss.redis.instance.hexists_used_times|分片hexists命令使用次数|Instance hexists Command Used Times|count/s|
jmiss.redis.instance.hget_used_times|分片hget命令使用次数|Instance hget Command Used Times|count/s|
jmiss.redis.instance.hgetall_used_times|分片hgetall命令使用次数|Instance hgetall Command Used Times|count/s|
jmiss.redis.instance.hincrby_used_times|分片hincrby命令使用次数|Instance hincrby Command Used Times|count/s|
jmiss.redis.instance.hincrbyfloat_used_times|分片hincrbyfloat命令使用次数|Instance hincrbyfloat Command Used Times|count/s|
jmiss.redis.instance.hkeys_used_times|分片hkeys命令使用次数|Instance hkeys Command Used Times|count/s|
jmiss.redis.instance.hlen_used_times|分片hlen命令使用次数|Instance hlen Command Used Times|count/s|
jmiss.redis.instance.hmget_used_times|分片hmget命令使用次数|Instance hmget Command Used Times|count/s|
jmiss.redis.instance.hmset_used_times|分片hmset命令使用次数|Instance hmset Command Used Times|count/s|
jmiss.redis.instance.hset_used_times|分片hset命令使用次数|Instance hset Command Used Times|count/s|
jmiss.redis.instance.hsetnx_used_times|分片hsetnx命令使用次数|Instance hsetnx Command Used Times|count/s|
jmiss.redis.instance.hvals_used_times|分片hvals命令使用次数|Instance hvals Command Used Times|count/s|
jmiss.redis.instance.hscan_used_times|分片hscan命令使用次数|Instance hscan Command Used Times|count/s|
jmiss.redis.instance.hdel_avg_rt |分片hdel命令平均响应时间|Instance hdel Command Average Response Time|us|
jmiss.redis.instance.hexists_avg_rt |分片hexists命令平均响应时间|Instance hexists Command Average Response Time | count/s
jmiss.redis.instance.hget_avg_rt|分片hget命令平均响应时间|Instance hget Command Average Response Time|count/s|
jmiss.redis.instance.hgetall_avg_rt|分片hgetall命令平均响应时间|Instance hgetall Command Average Response Time|us|
jmiss.redis.instance.hincrby_avg_rt|分片hincrby命令平均响应时间|Instance hincrby Command Average Response Time|us|
jmiss.redis.instance.hincrbyfloat_avg_rt|分片hincrbyfloat命令平均响应时间|Instance hincrbyfloat Command Average Response Time|us|
jmiss.redis.instance.hkeys_avg_rt|分片hkeys命令平均响应时间| Instance hkeys Command Average Response Time |us|
jmiss.redis.instance.hlen_avg_rt|分片hlen命令平均响应时间|Instance hlen Command Average Response Time|us|
jmiss.redis.instance.hmget_avg_rt|分片hmget命令平均响应时间|Instance hmget Command Average Response Time|us|
jmiss.redis.instance.hmset_avg_rt|分片hmset命令平均响应时间|Instance hmset Command Average Response Time|us|
jmiss.redis.instance.hset_avg_rt|分片hset命令平均响应时间|Instance hset Command Average Response Time|us|
jmiss.redis.instance.hsetnx_avg_rt|分片hsetnx命令平均响应时间|Instance hsetnx Command Average Response Time|us|
jmiss.redis.instance.hvals_avg_rt|分片hvals命令平均响应时间|Instance hvals Command Average Response Time|us|
jmiss.redis.instance.hscan_avg_rt|分片hscan命令平均响应时间|Instance hscan Command Average Response Time|us|
jmiss.redis.instance.hstrlen_used_times|分片hstrlen命令使用次数|Instance hstrlen Command Used Times|count/s|仅redis4.0 有该指标|
jmiss.redis.instance.hstrlen_avg_rt|分片hstrlen命令平均响应时间|Instance hstrlen Command Average Response Time|us|仅redis4.0 有该指标|


### Lists监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.instance.lindex_used_times|分片lindex命令使用次数|Instance lindex Command Used Times|count/s
jmiss.redis.instance.linsert_used_times|分片linsert命令使用次数|Instance linsert Command Used Times|count/s|
jmiss.redis.instance.llen_used_times|分片llen命令使用次数|Instance llen Command Used Times|count/s|
jmiss.redis.instance.lpop_used_times|分片lpop命令使用次数|Instance lpop Command Used Times|count/s|
jmiss.redis.instance.lpush_used_times|分片lpush命令使用次数|Instance lpush Command Used Times|count/s|
jmiss.redis.instance.lpushx_used_times|分片lpushx命令使用次数|Instance lpushx Command Used Times|count/s|
jmiss.redis.instance.lrange_used_times|分片lrange命令使用次数|Instance lrange Command Used Times|count/s|
jmiss.redis.instance.lrem_used_times|分片lrem命令使用次数|Instance lrem Command Used Times|count/s|
jmiss.redis.instance.lset_used_times|分片lset命令使用次数|Instance lset Command Used Times|count/s|
jmiss.redis.instance.ltrim_used_times|分片ltrim命令使用次数|Instance ltrim Command Used Times|count/s|
jmiss.redis.instance.rpop_used_times|分片rpop命令使用次数|Instance rpop Command Used Times|count/s|
jmiss.redis.instance.rpush_used_times|分片rpush命令使用次数|Instance rpush Command Used Times|count/s|
jmiss.redis.instance.rpushx_used_times|分片rpushx命令使用次数|Instance rpushx Command Used Times|count/s|
jmiss.redis.instance.lindex_avg_rt|分片lindex命令平均响应时间|Instance lindex Command Average Response Time|us|
jmiss.redis.instance.linsert_avg_rt|分片linsert命令平均响应时间|Instance linsert Command Average Response Time|us|
jmiss.redis.instance.llen_avg_rt|分片llen命令平均响应时间|Instance llen Command Average Response Time|us|
jmiss.redis.instance.lpop_avg_rt|分片lpop命令平均响应时间|Instance lpop Command Average Response Time|us|
jmiss.redis.instance.lpush_avg_rt|分片lpush命令平均响应时间|Instance lpush Command Average Response Time|us|
jmiss.redis.instance.lpushx_avg_rt|分片lpushx命令平均响应时间|Instance lpushx Command Average Response Time|us|
jmiss.redis.instance.lrange_avg_rt|分片lrange命令平均响应时间|Instance lrange Command Average Response Time|us|
jmiss.redis.instance.lrem_avg_rt|分片lrem命令平均响应时间|Instance lrem Command Average Response Time|us|
jmiss.redis.instance.lset_avg_rt|分片lset命令平均响应时间|Instance lset Command Average Response Time|us|
jmiss.redis.instance.ltrim_avg_rt|分片ltrim命令平均响应时间|Instance ltrim Command Average Response Time|us|
jmiss.redis.instance.rpop_avg_rt|分片rpop命令平均响应时间|Instance rpop Command Average Response Time|us|
jmiss.redis.instance.rpush_avg_rt|分片rpush命令平均响应时间|Instance rpush Command Average Response Time|us|
jmiss.redis.instance.rpushx_avg_rt|分片rpushx命令平均响应时间|Instance rpushx Command Average Response Time|us|

### Sets监控组

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
jmiss.redis.instance.sadd_used_times|分片sadd命令使用次数|Instance  sadd Command Used Times|count/s| 
jmiss.redis.instance.scard_used_times| 分片scard命令使用次数 |Instance  scard Command Used Times|count/s| 
jmiss.redis.instance.sismember_used_times|分片sismember命令使用次数|Instance  sismember Command Used Times|count/s|
jmiss.redis.instance.smembers_used_times|分片smembers命令使用次数|Instance  smembers Command Used Times|count/s|
jmiss.redis.instance.spop_used_times|分片spop命令使用次数|Instance  spop Command Used Times|count/s|
jmiss.redis.instance.srandmember_used_times|分片srandmember命令使用次数|Instance  srandmember Command Used Times|count/s|
jmiss.redis.instance.srem_used_times|分片srem命令使用次数|Instance  srem Command Used Times|count/s|
jmiss.redis.instance.sscan_used_times|分片sscan命令使用次数|Instance  sscan Command Used Times | count/s|
jmiss.redis.instance.sadd_avg_rt|分片sadd命令平均响应时间|Instance  sadd Command Average Response Time|us| 
jmiss.redis.instance.scard_avg_rt|分片scard命令平均响应时间|Instance  scard Command Average Response Time|us|
jmiss.redis.instance.sismember_avg_rt|分片sismember命令平均响应时间|Instance  sismember Command Average Response Time|us|
jmiss.redis.instance.smembers_avg_rt|分片smembers命令平均响应时间|Instance  smembers Command Average Response Time|us|
jmiss.redis.instance.spop_avg_rt|分片spop命令平均响应时间|Instance  spop Command Average Response Time|us|
jmiss.redis.instance.srandmember_avg_rt|分片srandmember命令平均响应时间|Instance  srandmember Command Average Response Time|us|
jmiss.redis.instance.srem_avg_rt|分片srem命令平均响应时间|Instance  srem Command Average Response Time|us|
jmiss.redis.instance.sscan_avg_rt|分片sscan命令平均响应时间|Instance  sscan Command Average Response Time|us|


