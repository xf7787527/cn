# createAccount


## 描述
创建一个Clickhouse账号

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountName**|String|True| |账号名|
|**accountPassword**|String|True| |密码|
|**privilege**|String|True| |账号权限|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
