# describeClusterList


## 描述
获取已接入mysql实例列表

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/hadcutin

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|
|**gid**|String|False| |实例gid|
|**instanceName**|String|False| |实例名称|
|**dbSource**|String|False| |接入来源|
|**status**|String|False| |实例状态|
|**dbType**|String|False| |实例类型，默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeclusterlist#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**checkOkCount**|Integer|连接正常数|
|**checkFailCount**|Integer|连接异常数|
|**data**|[InstancesInfo[]](describeclusterlist#instancesinfo)|列表|
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
