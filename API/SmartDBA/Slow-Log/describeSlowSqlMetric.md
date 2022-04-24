# describeSlowSqlMetric


## 描述
查询慢sql次数及分布

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/sqlMetrics

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**metric**|String|True| |metric名称|
|**startTime**|String|True| |查询开始时间，格式为：2021-11-11T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2021-11-11T15:04:05Z|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeslowsqlmetric#result)| |
|**requestId**|String|请求id|


### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**itemData**|[DataPoint[]](describeslowsqlmetric#datapoint)|监控值对|
|**metricInfo**|[Metric](describeslowsqlmetric#metric)|metric元信息|
### <div id="Metric">Metric</div>
|名称|类型|描述|
|---|---|---|
|**calculateUnit**|String|单位|
|**metric**|String|metric名称|
|**metricName**|String|metric中文名称|
|**metricDescribe**|String|metric功能描述|
### <div id="DataPoint">DataPoint</div>
|名称|类型|描述|
|---|---|---|
|**timestamp**|Long|时间戳，精确到毫秒，如：1606836371000。|
|**value**|String|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
