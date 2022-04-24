# modifyPrivilege


## 描述
修改账号权限

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:modifyPrivilege

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|
|**accountName**|String|True| |账号名称|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**privileges**|String|False| |账号的访问权限|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
