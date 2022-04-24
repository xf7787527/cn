# describeWhiteList


## 描述
查看实例当前白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/whiteList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describewhitelist#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**whiteLists**|[WhiteList[]](describewhitelist#whitelist)|白名单列表|
### <div id="whitelist">WhiteList</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|白名单名称|
|**ips**|String|IP或IP段，不同的IP/IP段之间用英文逗号分隔，例如0.0.0.0/0,192.168.0.10|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
