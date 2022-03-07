# historySql


## 描述
获取当前实例用户查询sql历史

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/historySql

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**pageNumber**|Integer|False| |显示数据的页码，取值范围：[1,∞)。pageNumber为Null时，返回所有数据页码；超过总页数时，无数据。|
|**pageSize**|Integer|False| |每页显示的数据条数，用于查询列表的接口。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**count**|Integer|历史sql总量|
|**historySqls**|[DmsHistorySql[]](#dmshistorysql)| |
### <div id="DmsHistorySql">DmsHistorySql</div>
|名称|类型|描述|
|---|---|---|
|**sql**|String|执行sql内容。|
|**user**|String|执行用户。|
|**status**|String|执行状态|
|**createTime**|String|创建时间，格式为：YYYY-MM-DD HH:mm:ss。|
|**spendTime**|Integer|执行花费时间，单位ms。|
|**message**|String|执行消息。|
|**database**|String|数据库名称。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
