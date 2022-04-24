# describeIndexs


## 描述
获取冗余索引和未使用索引的信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeIndexs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**indexType**|String|True| |索引类型|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeindexs#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[IndexInfo[]](describeindexs#indexinfo)|未使用索引列表|
### <div id="IndexInfo">IndexInfo</div>
|名称|类型|描述|
|---|---|---|
|**indexName**|String|索引名称|
|**db**|String|库名|
|**tableName**|String|表名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
