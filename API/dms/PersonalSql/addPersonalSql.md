# addPersonalSql


## 描述
收藏sql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/personalSql:add

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**sqlStr**|String|True| |收藏的sql语句。|
|**hint**|String|True| |备注。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](addpersonalsql#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|返回消息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
