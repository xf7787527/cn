# describeAccounts


## 描述
查看某个实例下的账号信息

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeaccounts#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accountName**|String|账号名称|
|**accountStatus**|String|账号状态("BUILDING","RUNNING","RESETING")|
|**createTime**|String|创建时间，格式为：YYYY-MM-DD HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
