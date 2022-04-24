# describeSlowDigestLog


## 描述
获取当前实例指定时间的慢SQL统计

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/slowDigestLog

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
|**sort**|String|False| |按queryCount的排序方式，默认desc|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeslowdigestlog#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[SlowDigestLog[]](describeslowdigestlog#slowdigestlog)| |
|**totalCount**|Integer|总数|
### <div id="SlowDigestLog">SlowDigestLog</div>
|名称|类型|描述|
|---|---|---|
|**execTime**|[Statistic](describeslowdigestlog#statistic)|执行时间|
|**lockTime**|[Statistic](describeslowdigestlog#statistic)|锁等待时间|
|**rowsSent**|[StatisticInt](describeslowdigestlog#statisticint)|返回行数|
|**rowsExamined**|[StatisticInt](describeslowdigestlog#statisticint)|扫描行数|
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

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
