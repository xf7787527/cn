# selectDetailList


## 描述
根据实例的的id，获取实例相关信息。

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances:selectDetailList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**resourceList**|String|True| |资源id列表（多个以,分隔）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](selectdetaillist#result)| |
|**requestId**|String| |
### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[ResourceInfo[]](selectdetaillist#resourceinfo)| |
### <div id="resourceinfo">ResourceInfo</div>
|名称|类型|描述|
|---|---|---|
|**resourceId**|String|实例ID|
|**resourceName**|String|实例名称|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
