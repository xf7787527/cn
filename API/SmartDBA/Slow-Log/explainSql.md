# explainSql


## 描述
SQL explain执行计划

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/explainSql

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**database**|String|True| |数据库名|
|**sql**|String|True| |SQL语句|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](explainsql#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[ExecutionPlan[]](explainsql#executionplan)| |
### <div id="ExecutionPlan">ExecutionPlan</div>
|名称|类型|描述|
|---|---|---|
|**id**|String|sql执行顺序id|
|**selectType**|String|select语句类型|
|**table**|String|表名|
|**partitions**|String|匹配的分区|
|**accessType**|String|访问行的类型|
|**possibleKeys**|String|可能选用的索引|
|**key**|String|确切使用到的索引|
|**keyLen**|String|表示索引中使用的字节数|
|**ref**|String|哪个字段或常数与 key 一起被使用|
|**rows**|String|一共扫描了多少行. 是一个估计值|
|**filtered**|String|此查询条件所过滤的数据的百分比|
|**extra**|String|额外的信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
