# generalCreateTableSql


## 描述
生成建表语句sql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/createSql:general

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名|
|**tableName**|String|True| |表名|
|**metaTableInfo**|[MetaTableInfo](#metatableinfo)|True| |表元信息。|
|**columnInfos**|[ColumnInfo[]](#columninfo)|True| |列信息。|
|**indexInfos**|[IndexInfo[]](#indexinfo)|False| |索引信息。|
|**extraTableInfo**|[ExtraTableInfo](#extratableinfo)|False| |分表信息，stardb数据源中使用。|

### <div id="ExtraTableInfo">ExtraTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableTypeEnum**|String|True| |ORIGIN:原始表, STARDB_SPLIT:stardb切分表, STARDB_ISOLATE:stardb孤立表, STARDB_BROADCAST:stardb广播表。|
|**stardbSplitInfo**|[StardbSplitInfo](#stardbsplitinfo)|False| |tableTypeEnum为切分表时的切分信息内容。|
### <div id="StardbSplitInfo">StardbSplitInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**splitType**|String|True| |切分方式，"MODULO：取模, "HASH"：哈希, "DB_TABLE"：分库分表, "YYYYMMDD","YYYYMM","MM","MMDD"|
|**tableSplitCount**|Integer|False| |切分表数量,表切分方式为哈希取模时必需|
|**columnNames**|String[]|True| |切分列名称，第一项为切分表的列（必需），第二项为切分库的列（非必需)|
|**splitDateBegin**|String|False| |起始时间，切分方式为时间时必需，格式为20220125|
|**splitDateEnd**|String|False| |结束时间，切分方式为时间时必需，格式为20220125|
### <div id="IndexInfo">IndexInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**indexName**|String|True| |索引名。|
|**indexType**|String|True| |列类型，普通索引：NORMAL，唯一索引：UNIQUE。|
|**columnNames**|String[]|True| |列名称。|
### <div id="ColumnInfo">ColumnInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**columnName**|String|True| |列名。|
|**newColumnName**|String|False| |新列名，修改表结构时使用。|
|**dataType**|String|True| |列类型。|
|**columnType**|String|False| |列类型, 返回int(3), varchar(64)等。|
|**columnLength**|Integer|False| |列长度。|
|**columnScale**|Integer|False| |浮点数小数点后位数。|
|**isNull**|Boolean|True| |是否为空。|
|**defaultValue**|String|False| |默认值。|
|**columnComment**|String|False| |列注释。|
|**isAutoIncrease**|Boolean|True| |是否自增。|
|**isPrimaryKey**|Boolean|True| |是否为主键。|
### <div id="MetaTableInfo">MetaTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableName**|String|True| |表名。|
|**tableComment**|String|False| |表注释。|
|**tableCharset**|String|True| |表字符编码。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|生成sql|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
