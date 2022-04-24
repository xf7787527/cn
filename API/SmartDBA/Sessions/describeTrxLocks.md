# describeTrxLocks


## 描述
获取事务锁信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeTrxLocks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describetrxlocks#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[LockStatistic[]](describetrxlocks#lockstatistic)|事务锁列表|
### <div id="LockStatistic">LockStatistic</div>
|名称|类型|描述|
|---|---|---|
|**table**|String|表|
|**holdLock**|Integer|持有锁的会话ID|
|**waitLock**|String|等待锁的会话ID|
|**startTime**|String|事务开始时间|
|**waitTime**|Integer|总等待时长|
|**waitSql**|String|等待锁的sql|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
