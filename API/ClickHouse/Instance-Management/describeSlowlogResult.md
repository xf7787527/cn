# describeSlowlogResult


## 描述
查询 Clickhouse audit列表信息

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/slowlog:describeSlowlogResult

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，用于查询列表的接口|
|**startTime**|String|False| |开始时间|
|**endTime**|String|False| |结束时间|
|**segmentName**|String|False| |节点名称|
|**queryTime**|String|False| |查询时间|
|**filters**|[Filter[]](describeslowlogresult#filter)|False| | |

<div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeslowlogresult#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**slowlogResult**|[SlowLog](describeslowlogresult#slowlog)| |
|**totalCount**|Number| |
<div id="slowlog">SlowLog</div>
|名称|类型|描述|
|---|---|---|
|**ip**|String|源IP|
|**requestId**|String|初始请求ID|
|**segmentName**|String|节点名称|
|**startTime**|String|SQL开始时间|
|**queryTime**|String|慢日志SQL执行时间|
|**sql**|String|SQL语句|
|**lineNumber**|Integer|读取慢日志SQL的行数|
|**dataSize**|String|读取慢日志SQL的数据量|
|**executingResult**|String|返回结果数据量大小|
|**memoryUsage**|String|返回结果内存使用量|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
