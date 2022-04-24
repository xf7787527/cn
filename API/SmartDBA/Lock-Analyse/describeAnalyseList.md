# describeAnalyseList


## 描述
获取当前实例的所有诊断记录

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/analyseList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|
|**startTime**|String|True| |查询开始时间，格式为：2006-01-02T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2006-01-02T15:04:05Z|
|**state**|Boolean|False| |是否只过滤死锁存在的记录|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeanalyselist#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[DeadLockOverview[]](describeanalyselist#deadlockoverview)|诊断记录概览列表|
### <div id="DeadLockOverview">DeadLockOverview</div>
|名称|类型|描述|
|---|---|---|
|**analyseId**|String|锁诊断id|
|**createTime**|String|诊断时间|
|**occurTime**|String|发生时间|
|**occured**|String|是否发现死锁|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
