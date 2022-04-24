# describeAllTableInfoForDb


## 描述
获取指定库下的所有表名

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/allTableInfoForDb

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbName**|String|False| |数据库名|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describealltableinfofordb#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|String[]|表名列表|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
