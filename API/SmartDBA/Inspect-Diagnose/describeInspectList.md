# describeInspectList


## 描述
获取实例的巡检记录列表

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/inspects

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |查询开始时间，格式为：2006-01-02T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2006-01-02T15:04:05Z|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|
|**instanceGid**|String|False| |实例id|
|**instanceName**|String|False| |实例名称|
|**dbType**|String|False| |实例类型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeinspectlist#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[InspectTaskModel[]](describeinspectlist#inspecttaskmodel)|列表|
### <div id="InspectTaskModel">InspectTaskModel</div>
|名称|类型|描述|
|---|---|---|
|**inspectId**|String|诊断id|
|**instanceId**|String|rds实例id|
|**instanceName**|String|rds实例名称|
|**instanceClass**|String|实例规格|
|**region**|String|区域|
|**instanceType**|String|实例类型|
|**engineVersion**|String|数据库版本|
|**score**|Integer|巡检分值|
|**beginTime**|String|巡检范围的起始时间，如：2020-11-09T00:00:00Z|
|**endTime**|String|巡检范围的截至时间，如：2020-11-09T23:59:59Z|
|**createTime**|String|巡检开始时间，2021-11-09T00:19:00Z|
|**updateTime**|String|巡检完成时间，2021-11-09T00:19:30Z|
|**cupInfo**|String|cpu使用率|
|**memoryInfo**|String|内存使用率|
|**connectInfo**|String|连接使用率|
|**slowSqlInfo**|String|慢SQL数量|
|**bigTableInfo**|String|大表数量|
|**deadLockInfo**|String|是否死锁|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
