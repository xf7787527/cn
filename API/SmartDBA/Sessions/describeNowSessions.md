# describeNowSessions


## 描述
获取实时会话信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeNowSessions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describenowsessions#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[NowSession[]](describenowsessions#nowsession)|实时会话列表|
### <div id="NowSession">NowSession</div>
|名称|类型|描述|
|---|---|---|
|**id**|Integer|会话id|
|**user**|String|会话用户|
|**host**|String|会话源端IP|
|**db**|String|数据库|
|**command**|String|session命令|
|**time**|Integer|会话活跃时间|
|**state**|String|会话状态|
|**info**|String|正在执行的sql|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
