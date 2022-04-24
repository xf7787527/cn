# modifyWhiteList


## 描述
修改允许访问实例的IP白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。

## 请求方式
PUT

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/whiteList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ips**|String|True| |IP或IP段，不同的IP/IP段之间用英文逗号分隔，例如0.0.0.0/0,192.168.0.10|
|**name**|String|True| |白名单分组名|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
