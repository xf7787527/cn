# describeSchemaSpaceTop


## 描述
库空间Top 10

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/schemaSpaceTop

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sortField**|String|False| |排序字段：表空间(totalSize)、表数据空间(dataSize)、索引空间(idxSize)、碎片率(fragment)、行数(dataRows)|
|**sortType**|String|False| |排序类型，desc 降序、asc 升序，默认降序|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeschemaspacetop#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[TableStorageInfo[]](describeschemaspacetop#tablestorageinfo)|库空间信息Top 列表|
### <div id="TableStorageInfo">TableStorageInfo</div>
|名称|类型|描述|
|---|---|---|
|**tableName**|String|表名|
|**dbName**|String|数据库名|
|**engine**|String|引擎|
|**totalSize**|String|表空间大小|
|**percentage**|String|表空间占比|
|**dataSize**|String|数据空间|
|**idxSize**|String|索引空间|
|**fragment**|String|碎片率|
|**dataRows**|Integer|表行数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
