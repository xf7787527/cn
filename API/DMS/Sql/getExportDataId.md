# getExportDataId


## 描述
获取数据导出Id

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:getExportDataId

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**sql**|String|True| |导出数据的查询sql|
|**dbName**|String|True| |数据库名称|
|**count**|Integer|True| |导出数量|
|**ignoreCheck**|Boolean|True| |是否跳过检测|
|**reason**|String|False| |跳过行数检测原因|
|**charset**|String|True| |导出文件字符编码|
|**exportTypeEnum**|String|True| |导出方式，SYNC("SYNC", 0), ASYNC("ASYNC", 1)，当前只支持SYNC导出;|
|**exportFileTypeEnum**|String|True| |导出文件格式，CSV("CSV", 0), SQL("SQL", 1);|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|导出文件下载id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
