# describeInspect


## 描述
获取巡检记录

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/inspects/{inspectId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**inspectId**|String|True| |巡检任务id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeinspect#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**score**|Integer|巡检分值|
|**beginTime**|String|巡检范围的起始时间，如：2021-11-09T00:00:00Z|
|**endTime**|String|巡检范围的截至时间，如：2021-11-09T23:59:59Z|
|**systemView**|[SystemView](describeinspect#systemview)|资源使用率|
|**connectView**|[ConnectView](describeinspect#connectview)|连接数|
|**engineView**|[EngineView](describeinspect#engineview)|锁信息|
|**schemaView**|[SchemaView](describeinspect#schemaview)|库表空间|
|**diskView**|[DiskView](describeinspect#diskview)|磁盘空间|
|**slowLowView**|[SlowLowView](describeinspect#slowlowview)|慢sql|
|**detail**|[KV[]](describeinspect#kv)|扣分明细|
### <div id="KV">KV</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**value**|String|值|
### <div id="SlowLowView">SlowLowView</div>
|名称|类型|描述|
|---|---|---|
|**items**|[SlowDigestLog[]](describeinspect#slowdigestlog)| |
|**message**|String|扣分说明|
### <div id="SlowDigestLog">SlowDigestLog</div>
|名称|类型|描述|
|---|---|---|
|**execTime**|[Statistic](describeinspect#statistic)|执行时间|
|**lockTime**|[Statistic](describeinspect#statistic)|锁等待时间|
|**rowsSent**|[StatisticInt](describeinspect#statisticint)|返回行数|
|**rowsExamined**|[StatisticInt](describeinspect#statisticint)|扫描行数|
|**sql**|String|sql模板|
|**database**|String|数据库|
|**queryCount**|Integer|执行次数|
### <div id="StatisticInt">StatisticInt</div>
|名称|类型|描述|
|---|---|---|
|**avg**|Integer|平均值|
|**max**|Integer|最大值|
|**sum**|Integer|和|
### <div id="Statistic">Statistic</div>
|名称|类型|描述|
|---|---|---|
|**avg**|Float|平均值|
|**max**|Float|最大值|
|**sum**|Float|和|
### <div id="DiskView">DiskView</div>
|名称|类型|描述|
|---|---|---|
|**totalSize**|String|总空间|
|**usedSize**|String|已用空间|
|**dayIncrease**|String|日增空间|
|**dayRatio**|String|空间日增率|
|**message**|String|扣分说明|
### <div id="SchemaView">SchemaView</div>
|名称|类型|描述|
|---|---|---|
|**items**|[TableStorage[]](describeinspect#tablestorage)|表空间，top10|
|**message**|String|扣分说明|
### <div id="TableStorage">TableStorage</div>
|名称|类型|描述|
|---|---|---|
|**tableName**|String|表名|
|**dbName**|String|数据库名|
|**engine**|String|引擎类型|
|**totalSize**|String|表空间|
|**percentage**|String|表空间占比，如 40%|
|**dataSize**|String|数据空间|
|**idxSize**|String|索引空间|
|**fragment**|String|碎片率，如 0.99%|
|**dataRows**|Integer|表行数|
### <div id="EngineView">EngineView</div>
|名称|类型|描述|
|---|---|---|
|**deadLock**|String|死锁次数|
|**rowsLockAwaits**|String|锁等待次数|
|**rowsLockTime**|String|锁平均等待时间，单位ms|
|**message**|String|扣分说明|
### <div id="ConnectView">ConnectView</div>
|名称|类型|描述|
|---|---|---|
|**running**|[StatisticString](describeinspect#statisticstring)|活跃连接数|
|**total**|[StatisticString](describeinspect#statisticstring)|总连接数|
|**max**|String|最大连接数|
|**ratio**|[StatisticString](describeinspect#statisticstring)|连接使用率|
|**message**|String|扣分说明|
### <div id="StatisticString">StatisticString</div>
|名称|类型|描述|
|---|---|---|
|**avg**|String|平均值|
|**max**|String|最大值|
|**sum**|String|和|
### <div id="SystemView">SystemView</div>
|名称|类型|描述|
|---|---|---|
|**cpu**|[StatisticString](describeinspect#statisticstring)|cpu|
|**mem**|[StatisticString](describeinspect#statisticstring)|内存|
|**iops**|[StatisticString](describeinspect#statisticstring)|每秒读写次数|
|**message**|String|扣分说明|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
