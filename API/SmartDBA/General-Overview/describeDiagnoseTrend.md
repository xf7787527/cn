# describeDiagnoseTrend


## 描述
一键诊断趋势

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/diagnoseTrend

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询时间，格式为：2021-11-11T15:04:05Z|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describediagnosetrend#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DataPoint[]](describediagnosetrend#datapoint)|键值对|
### <div id="DataPoint">DataPoint</div>
|名称|类型|描述|
|---|---|---|
|**timestamp**|Long|时间戳，精确到毫秒，如：1606836371000。|
|**value**|String|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
