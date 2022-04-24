# createLockAnalyse


## 描述
死锁诊断

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/lockAnalyse

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createlockanalyse#result)| |
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**analyseId**|String|锁诊断id|
|**state**|String|诊断完成状态：complete\fail|
|**message**|String|状态说明信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
