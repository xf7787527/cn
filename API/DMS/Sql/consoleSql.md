# consoleSql


## 描述
执行sql语句

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/console:exeSql

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称|
|**sqls**|String|True| |sql语句。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**error**|[Error](#error)| |

### <div id="Error">Error</div>
|名称|类型|描述|
|---|---|---|
|**code**|Integer|错误码，-1：执行错误，-2：需要重新登录|
### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqlResults**|[DmsSqlResult[]](#dmssqlresult)|查询结果。|
### <div id="DmsSqlResult">DmsSqlResult</div>
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
