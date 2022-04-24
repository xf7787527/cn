# getCreateTableBatchSql


## 描述
获取批量建表sql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:getCreateTableBatchSql

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**createTableInfos**|[CreateTableInfo[]](getcreatetablebatchsql#createtableinfo)|False| |查询结果。|

### <div id="createtableinfo">CreateTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sql**|String|True| |sql语句。|
|**extraTableInfo**|[ExtraTableInfo](getcreatetablebatchsql#extratableinfo)|False| |创建广播表，分表额外信息。|
### <div id="extratableinfo">ExtraTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableTypeEnum**|String|True| |ORIGIN:原始表, STARDB_SPLIT:stardb切分表, STARDB_ISOLATE:stardb孤立表, STARDB_BROADCAST:stardb广播表。|
|**stardbSplitInfo**|[StardbSplitInfo](getcreatetablebatchsql#stardbsplitinfo)|False| |tableTypeEnum为切分表时的切分信息内容。|
### <div id="stardbsplitinfo">StardbSplitInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**splitType**|String|True| |切分方式，"MODULO：取模, "HASH"：哈希, "DB_TABLE"：分库分表, "YYYYMMDD","YYYYMM","MM","MMDD"|
|**tableSplitCount**|Integer|False| |切分表数量,表切分方式为哈希取模时必需|
|**columnNames**|String[]|True| |切分列名称，第一项为切分表的列（必需），第二项为切分库的列（非必需)|
|**splitDateBegin**|String|False| |起始时间，切分方式为时间时必需，格式为20220125|
|**splitDateEnd**|String|False| |结束时间，切分方式为时间时必需，格式为20220125|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getcreatetablebatchsql#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|格式化后的SQL|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
