# cancleConnect


## 描述
取消实例接入

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/cancelinstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**gidList**|String[]|True| |取消的实例gid列表|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](cancleconnect#result)| |
|**requestId**|String|请求id|


### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[InstancesInfo[]](cancleconnect#instancesinfo)|列表|
### <div id="InstancesInfo">InstancesInfo</div>
|名称|类型|描述|
|---|---|---|
|**clusterGid**|String|rds实例id|
|**port**|Integer|端口号|
|**name**|String|rds实例名称|
|**engineVersion**|String|数据库版本, 如： MySQL|
|**instanceType**|String|实例类型，如：cluster，standalone|
|**instanceStatus**|String|接入状态|
|**message**|String|接入状态描述|
|**source**|String|接入来源，目前默认rds|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
