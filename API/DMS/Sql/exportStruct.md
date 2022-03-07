# exportStruct


## 描述
表结构导出

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:exportStruct

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**tableName**|String|False| |导出表名，为空时导出库中所有表|
|**charset**|String|True| |导出文件字符编码|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**tableStructs**|[TableStruct[]](#tablestruct)|查询结果。|
### <div id="TableStruct">TableStruct</div>
|名称|类型|描述|
|---|---|---|
|**tableName**|String|表名。|
|**tableStruct**|String|建表语句。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
