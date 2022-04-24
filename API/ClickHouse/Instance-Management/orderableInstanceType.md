# orderableInstanceType


## 描述
获取当前用户售罄信息

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/OrderableInstanceType

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](orderableinstancetype#result)| |
|**requestId**|String| |
### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**engineStatus**|Integer| |
|**orderableAZs**|[Az[]](orderableinstancetype#az)| |
### <div id="az">Az</div>
|名称|类型|描述|
|---|---|---|
|**azId**|String|az名称|
|**azStatus**|Integer|1正常0售罄|
|**orderableStorageTypes**|[Disk[]](orderableinstancetype#disk)| |
### <div id="disk">Disk</div>
|名称|类型|描述|
|---|---|---|
|**storageType**|String|disk名称|
|**storageTypeStatus**|Integer|1正常0售罄|
|**orderableinstanceClasses**|[Flavor[]](orderableinstancetype#flavor)| |
### <div id="flavor">Flavor</div>
|名称|类型|描述|
|---|---|---|
|**instanceClass**|String|flavor名称|
|**status**|Integer| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
