# importDdlDml


## 描述
sql导入

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:import

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**charset**|String|False| |上传文件编码|
|**sqls**|String|True| |sql语句|
|**sqlConsoleTypeEnum**|String|True| |sql类型, CREATE("CREATE", 0), ALTER_DATA("ALTER_DATA", 1), ALTER_STRUCT("ALTER_STRUCT", 2), DROP("DROP", 4), CONSOLE("CONSOLE", 5), BATCH_CREATE("BATCH_CREATE", 6), IMPORT_DATA("IMPORT_DATA", 7), EXPORT_STRUCT_DATA("EXPORT_STRUCT_DATA", 8);|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
