# describeAlarmResource


## 描述
近一小时告警列表，按级别倒序

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/describeAlarmResource

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10|
|**dbType**|String|False| |数据库类型，默认MySQL|
|**endTime**|String|True| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describealarmresource#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[AlarmDetail[]](describealarmresource#alarmdetail)|列表|
|**totalCount**|Integer|总数|
### <div id="AlarmDetail">AlarmDetail</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例id|
|**instanceName**|String|实例名称|
|**metric**|String|监控项|
|**triggerCondition**|String|触发条件|
|**alarmLevel**|String|告警级别，从低到高为‘告警’，‘严重’，‘致命’|
|**alarmLevelTag**|String|告警级别标记|
|**firstAlarmTime**|String|首次告警时间|
|**lastAlarmTime**|String|最近一次告警时间|
|**durationTime**|Integer|持续时间，单位：min|
|**frequency**|Integer|发生次数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
