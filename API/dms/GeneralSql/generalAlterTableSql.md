# generalAlterTableSql


## 描述
生成修改表结构语句sql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/alterSql:general

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源Id|
|**dbName**|String|True| |数据库名|
|**tableName**|String|True| |表名|
|**metaTableInfo**|[MetaTableInfo](generalaltertablesql#metatableinfo)|True| |表元信息。|
|**columnInfos**|[ColumnInfo[]](generalaltertablesql#columninfo)|False| |列信息。|
|**indexInfos**|[IndexInfo[]](generalaltertablesql#indexinfo)|False| |索引信息。|

### <div id="indexinfo">IndexInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**indexName**|String|True| |索引名。|
|**indexType**|String|True| |列类型，普通索引：NORMAL，唯一索引：UNIQUE。|
|**columnNames**|String[]|True| |列名称。|
### <div id="columnInfo">ColumnInfo</div>
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
### <div id="metatableinfo">MetaTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableName**|String|True| |表名。|
|**tableComment**|String|False| |表注释。|
|**tableCharset**|String|True| |表字符编码。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](generalaltertablesql#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|生成sql|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
