# resetPassword


## 描述
重置数据库账号密码

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:resetPassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|
|**accountName**|String|True| |账号名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPassword**|String|False| |新密码|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
