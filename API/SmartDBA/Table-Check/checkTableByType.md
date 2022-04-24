# checkTableByType


## 描述
根据诊断id进行表诊断

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/checkTables

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**checkTypeId**|Long|True| |诊断类型id|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)  pageIndex 为-1时，返回所有数据页码|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checktablebytype#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[FieldList[]](checktablebytype#fieldlist)|诊断结果|
|**totalCount**|Integer|总条数|
### <div id="FieldList">FieldList</div>
|名称|类型|描述|
|---|---|---|
|**dbName**|String|数据库名|
|**tableName**|String|表名|
|**engine**|String|表引擎|
|**keyType**|String|主键类型|
|**rowName**|String|列名|
|**rowType**|String|列类型|
|**tableRows**|Long|表行数|
|**tableSize**|Long|表存储大小|
|**indexName**|String|索引名|
|**indexRow**|String|索引的列|
|**number**|Long|个数|
|**sql**|String|操作sql|
|**autoIncrement**|String|当前自增序列值|
|**maxNum**|String|最大序列值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
