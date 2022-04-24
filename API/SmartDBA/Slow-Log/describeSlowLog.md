# describeSlowLog


## 描述
获取当前实例指定时间的慢SQL明细

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/slowLog

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |查询开始时间，格式为：2006-01-02T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2006-01-02T15:04:05Z|
|**dbName**|String|False| |过滤条件：数据库名|
|**userName**|String|False| |过滤条件：client 用户名|
|**clientIP**|String|False| |过滤条件：client IP|
|**keyword4Search**|String|False| |模糊查询关键字，只支持单个单词|
|**field**|String|False| |排序的字段，支持 execTime,lockTime,rowsExamined,rowsSent,startTime 默认是 startTime|
|**sort**|String|False| |排序方式，默认desc|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeslowlog#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[SlowLog[]](describeslowlog#slowlog)| |
|**totalCount**|Integer|总数|
### <div id="SlowLog">SlowLog</div>
|名称|类型|描述|
|---|---|---|
|**startTime**|String|开始时间|
|**userName**|String|用户名|
|**execTime**|Float|执行时间(秒)|
|**lockTime**|Float|锁等待时间(秒)|
|**rowsSent**|Float|返回行数|
|**rowsExamined**|Float|扫描行数|
|**sql**|String|sql语句|
|**database**|String|数据库名|
|**host**|String|客户端IP|
|**logType**|String|日志类型|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
