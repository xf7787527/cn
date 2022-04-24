# describeStorages


## 描述
获取空间信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeStorages

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describestorages#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalDiskSize**|String|总空间(单位：G)|
|**usedDiskSize**|String|已用空间(单位：G)|
|**totalIncreaseSize**|String|最近一周增长量(单位：G)|
|**averageIncrease**|String|最近一周平均增长率|
|**freeDiskSize**|String|剩余空间(单位：G)|
|**predictAvailableDays**|String|预计剩余可用天数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
