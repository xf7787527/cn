# modifyInstanceName


## 描述
修改实例名称。

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceName

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |实例名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
