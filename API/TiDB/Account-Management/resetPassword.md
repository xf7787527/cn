# resetPassword


## 描述
创建数据库账号，用户可以使用客户端，应用程序等通过该账号和密码登录RDS数据库实例。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:resetPassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|
|**accountName**|String|True| |账号名，在同一个实例中账号名不能重复|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPassword**|String|True| |新密码|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
