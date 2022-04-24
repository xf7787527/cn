# describeLockAnalyse


## 描述
获取锁诊断详情

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/lockAnalyse

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**analyseId**|String|True| |锁诊断Id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describelockanalyse#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**analyseId**|String|锁诊断记录Id|
|**occurTime**|String|锁发生时间|
|**deadLockLog**|String|死锁日志详情|
|**data**|[DeadLockDetail[]](describelockanalyse#deadlockdetail)|锁分析信息列表|
### <div id="DeadLockDetail">DeadLockDetail</div>
|名称|类型|描述|
|---|---|---|
|**trxName**|String|事务标记名称|
|**sessionId**|String|Session ID|
|**queryType**|String|请求类型|
|**trxId**|String|事务id|
|**host**|String|访问来源host|
|**tableName**|String|涉及表名|
|**waitLock**|String|等待锁|
|**waitLockIndex**|String|等待锁索引名|
|**waitLockType**|String|等待锁类型|
|**holdLock**|String|持有锁|
|**holdLockIndex**|String|持有锁索引名|
|**holdLockType**|String|持有锁类型|
|**trxSql**|String|事务SQL|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
