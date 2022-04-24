# historyImportData


## 描述
获取当前实例用户查询导入数据sql历史

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/historyImportData

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|False| |数据库名称|
|**pageNumber**|Integer|False| |显示数据的页码，取值范围：[1,∞)。pageNumber为Null时，返回所有数据页码；超过总页数时，无数据。|
|**pageSize**|Integer|False| |每页显示的数据条数，用于查询列表的接口。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](historyimportdata#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**count**|Integer|历史sql总量|
|**historySqls**|[HistorySql[]](historyimportdata#historysql)| |
### <div id="historysql">HistorySql</div>
|名称|类型|描述|
|---|---|---|
|**id**|Integer|主键id。|
|**dataSourceId**|Integer|数据源id。|
|**sqlStr**|String|执行sql内容。|
|**user**|String|执行用户。|
|**status**|String|数据状态。0：有效，1：无效|
|**createTime**|String|创建时间，格式为：YYYY-MM-DD HH:mm:ss。|
|**spendTime**|Integer|执行花费时间。|
|**message**|String|执行消息。|
|**ip**|String|dms执行地址。|
|**dbName**|String|数据库名称。|
|**endTime**|String|执行结束时间，格式为：YYYY-MM-DD HH:mm:ss。|
|**exeStatus**|String|执行结果，SUCCESS：成功，FAILED失败。|
|**sqlType**|String|sql类型, CREATE("CREATE", 0), ALTER_DATA("ALTER_DATA", 1), ALTER_STRUCT("ALTER_STRUCT", 2), DROP("DROP", 4), CONSOLE("CONSOLE", 5), BATCH_CREATE("BATCH_CREATE", 6), IMPORT_DATA("IMPORT_DATA", 7), EXPORT_STRUCT_DATA("EXPORT_STRUCT_DATA", 8);|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
