# describeSlowLogDimensionsStatistic


## 描述
获取实例时间范围内按 dbName、userName、clientIP 分组统计的慢sql条数信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/SlowLogDimensionsStatistic

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |查询开始时间，格式为：2021-11-12T15:04:05Z|
|**endTime**|String|True| |查询截止时间，格式为：2021-11-11T15:04:05Z|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeslowlogdimensionsstatistic#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dbName**|Map|数据库名信息|
|**userName**|Map|访问的用户名信息|
|**clientIP**|Map|客户端IP信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
