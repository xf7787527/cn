# disableInternetAccess


## 描述
关闭实例的外网访问功能。

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:disableInternetAccess

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**serviceType**|String|True| |服务类型（database/monitor）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
