# SmartDBA v2 API


## 简介
SmartDBA T-paas版API,包含rds实例接入及展示、Metric查询、会话信息等


### 版本
v2


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**bindMetrics**|POST|关联实例自定义监控项，每次都要求全量提交|
|**cancleConnect**|POST|取消实例接入|
|**checkTableByType**|GET|根据诊断id进行表诊断|
|**checkTableTypes**|GET|查询支持诊断的类型|
|**createCluster**|POST|新接入mysql实例|
|**createDiagnose**|POST|一键诊断|
|**createLockAnalyse**|POST|死锁诊断|
|**createPanel**|POST|添加监控大盘|
|**deletePanel**|DELETE|删除监控大盘|
|**describeAlarmHistory**|GET|查询告警历史|
|**describeAlarmResource**|GET|近一小时告警列表，按级别倒序|
|**describeAlarmStatistic**|GET|最近3小时，24小时，3天报警数量|
|**describeAlarmTrend**|GET|获取告警数量，用于趋势展示|
|**describeAllDbInfo**|GET|实例所有的库名|
|**describeAllTableInfoForDb**|GET|获取指定库下的所有表名|
|**describeAnalyseList**|GET|获取当前实例的所有诊断记录|
|**describeClusterDetail**|GET|获取实例详情|
|**describeClusterList**|GET|获取已接入mysql实例列表|
|**describeDiagnose**|GET|获取诊断记录|
|**describeDiagnoseList**|GET|获取当前实例的所有诊断记录|
|**describeDiagnoseTopResource**|GET|获取一键诊断分数最低的top5|
|**describeDiagnoseTrend**|GET|一键诊断趋势|
|**describeIndexs**|GET|获取冗余索引和未使用索引的信息|
|**describeInspect**|GET|获取巡检记录|
|**describeInspectList**|GET|获取实例的巡检记录列表|
|**describeLockAnalyse**|GET|获取锁诊断详情|
|**describeMetricValueByGid**|GET|查询监控值|
|**describeNowSessions**|GET|获取实时会话信息|
|**describePanelList**|GET|获取监控大盘列表|
|**describePanelMetricValueByGid**|GET|查询监控大盘监控值|
|**describeSchemaSpaceTop**|GET|库空间Top 10|
|**describeSessions**|GET|获取当前实例的会话信息|
|**describeSlowDigestLog**|GET|获取当前实例指定时间的慢SQL统计|
|**describeSlowLog**|GET|获取当前实例指定时间的慢SQL明细|
|**describeSlowLogDimensionsStatistic**|GET|获取实例时间范围内按 dbName、userName、clientIP 分组统计的慢sql条数信息|
|**describeSlowSqlMetric**|GET|查询慢sql次数及分布|
|**describeStorageTrend**|GET|获取空间趋势|
|**describeStorages**|GET|获取空间信息|
|**describeSupportMetrics**|GET|查询支持自定义的监控指标|
|**describeSystemInfo**|GET|获取当前实例系统信息|
|**describeTableSpaceDetail**|GET|空间明细|
|**describeTableSpaceTop**|GET|表空间Top 10|
|**describeTrxLocks**|GET|获取事务锁信息|
|**describeUnCommitTrxs**|GET|获取未提交事务信息|
|**describeUntrxLocks**|GET|获取非事务锁信息|
|**describeslowLogStatistic**|GET|最近3小时，24小时，3天慢sql情况|
|**explainSql**|POST|SQL explain执行计划|
|**getBindMetrics**|GET|查询实例已经绑定的监控项|
|**getPanelRelateClusters**|GET|获取关联实例|
|**getTopResourceByMetric**|GET|最近5分钟(或历史某点5分钟)，top5的资源|
|**killSession**|POST|kill当前实例指定的会话|
|**toBeConnectClusters**|GET|获取待接入的mysql实例|
|**turningSql**|POST|SQL优化|
|**updatePanelClusters**|POST|修改关联实例，每次都是全量下发|
