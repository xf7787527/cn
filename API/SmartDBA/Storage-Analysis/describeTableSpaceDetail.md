# describeTableSpaceDetail


## 描述
空间明细

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/tableSpaceDetail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sortField**|String|False| |排序字段：表空间(totalSize)、表数据空间(dataSize)、索引空间(idxSize)、碎片率(fragment)、行数(dataRows)|
|**sortType**|String|False| |排序类型，desc 降序、asc 升序，默认降序|
|**dbName**|String|False| |过滤的数据库名|
|**tableName**|String|False| |过滤的表名|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describetablespacedetail#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[TableStorageInfo[]](describetablespacedetail#tablestorageinfo)|库空间信息列表|
|**totalCount**|Integer|总数|
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
