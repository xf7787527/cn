# getExportId


## 描述
生成表结构数据导出下载Id

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:getExportId

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**charset**|String|True| |导出文件字符编码|
|**exportTypeEnum**|String|True| |导出方式，SYNC("SYNC", 0), ASYNC("ASYNC", 1)，当前只支持SYNC导出;|
|**exportFileTypeEnum**|String|True| |导出文件格式，CSV("CSV", 0), SQL("SQL", 1);|
|**exportContentTypeEnum**|String|True| |导出内容，DATA("DATA", 0), STRUCT("STRUCT", 1), STRUCT_DATA("STRUCT_DATA", 2);|
|**tableFilters**|[TableFilter[]](getexportid#tablefilter)|False| |查询条件。|

### <div id="tablefilter">TableFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableName**|String|False| |表名。|
|**filter**|String|False| |查询条件。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getexportid#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|导出文件下载id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
