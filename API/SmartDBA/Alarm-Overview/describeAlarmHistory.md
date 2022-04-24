# describeAlarmHistory


## 描述
查询告警历史

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/describeAlarmHistory

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10|
|**startTime**|String|True| |查询开始时间，格式为：2021-11-11T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2021-11-11T15:04:05Z|
|**dbType**|String|False| |数据库类型，默认MySQL|
|**instanceGid**|String|False| |实例Id|
|**instanceName**|String|False| |实例名称|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describealarmhistory#result)| |
|**requestId**|String|请求的标识id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[AlarmHistoryDetail[]](describealarmhistory#alarmhistorydetail)|告警历史列表|
|**totalCount**|Integer|总数|
### <div id="AlarmHistoryDetail">AlarmHistoryDetail</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例id|
|**instanceName**|String|实例名称|
|**metric**|String|监控项|
|**triggerCondition**|String|触发条件|
|**alarmLevel**|String|告警级别，从低到高为‘告警’，‘严重’，‘致命’|
|**alarmLevelTag**|String|告警级别标记|
|**alarmTime**|String|告警时间|
|**durationTime**|String|持续时间，单位：min|

## 返回码
|返回码|描述|
|---|---|
|**200**|查询告警历史|
