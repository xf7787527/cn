# describeAlarmStatistic


## 描述
最近3小时，24小时，3天报警数量

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/alarmStatistic

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询时间，格式为：2021-11-11T15:04:05Z|
|**dbType**|String|False| |数据库类型，默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describealarmstatistic#result)| |
|**requestId**|String|请求id|


### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**count3h**|Integer|最近3小时告警数量|
|**count24h**|Integer|最近24小时告警数量|
|**count72h**|Integer|最近72小时告警数量|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
