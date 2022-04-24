# consoleGeneralData


## 描述
生成数据

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:generalData

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**tableName**|String|True| |表名。|
|**count**|Integer|True| |生成数据行数。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](consolegeneraldata#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqlsResult**|[DmsSqlsResult](consolegeneraldata#dmssqlsresult)| |
### <div id="dmssqlsresult">DmsSqlsResult</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqlResults**|[DmsSqlResult[]](consolegeneraldata#dmssqlresult)|多条sql查询结果。|
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
