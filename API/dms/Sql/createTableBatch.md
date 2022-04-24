# createTableBatch


## 描述
批量建表

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:createTableBatch

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**createTableInfos**|[CreateTableInfo[]](createtablebatch#createtableinfo)|False| |查询结果。|

### <div id="createtableinfo">CreateTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sql**|String|True| |sql语句。|
|**extraTableInfo**|[ExtraTableInfo](createtablebatch#extratableinfo)|False| |创建广播表，分表额外信息。|
### <div id="extratableinfo">ExtraTableInfo</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tableTypeEnum**|String|True| |ORIGIN:原始表, STARDB_SPLIT:stardb切分表, STARDB_ISOLATE:stardb孤立表, STARDB_BROADCAST:stardb广播表。|
|**stardbSplitInfo**|[StardbSplitInfo](createtablebatch#stardbsplitinfo)|False| |tableTypeEnum为切分表时的切分信息内容。|
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
|**result**|[Result](createtablebatch#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqlsResult**|[DmsSqlsResult](createtablebatch#dmssqlsresult)| |
### <div id="dmssqlsresult">DmsSqlsResult</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqlResults**|[DmsSqlResult[]](createtablebatch#dmssqlresult)|多条sql查询结果。|
### <div id="dmssqlresult">DmsSqlResult</div>
|名称|类型|描述|
|---|---|---|
|**sqlType**|String|sql类型，SYNCDMLDDL，同步执行ddl，dml语句；ASYNCDMLDDL，异步执行ddl，dml语句，未支持；QUERY，执行查询类sql语句，如select；COMMAND，如show等命令，未支持。|
|**sql**|String|执行sql语句。|
|**retCode**|Integer|执行是否成功。|
|**message**|String|执行消息。|
|**queryResult**|Object[]|QUERY类型sql查询结果|
|**result**|Integer|SYNCDMLDDL，COMMAND类型SQL查询结果。|
|**total**|Integer|总执行sql条数。|
|**index**|Integer|当前结果是第几条sql。|
|**time**|Integer|执行时长，单位ms。|
|**affectCount**|Integer|查询到sql条数或影响行数。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
