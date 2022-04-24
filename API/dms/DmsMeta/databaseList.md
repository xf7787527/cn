# databaseList


## 描述
获取数据库实例的库列表

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/consoleDbList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](databaselist#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**databaseNames**|String[]|库名称列表|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
