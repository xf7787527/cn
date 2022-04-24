# describeStorageTrend


## 描述
获取空间趋势

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeStorageTrend

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |查询开始时间，格式为：2006-01-02T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2006-01-02T15:04:05Z|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describestoragetrend#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[MetricData[]](describestoragetrend#metricdata)|空间信息|
### <div id="MetricData">MetricData</div>
|名称|类型|描述|
|---|---|---|
|**itemData**|[DataPoint[]](describestoragetrend#datapoint)|监控值对|
|**metricInfo**|[Metric](describestoragetrend#metric)|metric元信息|
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
|**value**|Object|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
