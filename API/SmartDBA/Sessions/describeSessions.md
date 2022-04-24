# describeSessions


## 描述
获取当前实例的会话信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeSessions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describesessions#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**upTime**|Integer|实例已运行时间，单位:s|
|**activeSession**|Integer|运行中会话总数|
|**maxActiveTime**|Integer|运行中会话最长时间|
|**waitSession**|Integer|存在事务等待的会话|
|**totalSession**|Integer|会话总数|
|**systemsSession**|Integer|DMS（系统）会话总数|
|**totalCount**|Integer|总数|
|**sessions**|[Session[]](describesessions#session)|实时会话列表|
|**userStatistics**|[UserStatistic[]](describesessions#userstatistic)|按用户统计|
|**hostStatistics**|[HostStatistic[]](describesessions#hoststatistic)|按访问来源统计|
|**dbStatistics**|[DBStatistic[]](describesessions#dbstatistic)|按数据库统计|
### <div id="DBStatistic">DBStatistic</div>
|名称|类型|描述|
|---|---|---|
|**db**|String|数据库|
|**activeCount**|Integer|活跃会话总数|
|**threadIdList**|String|会话id列表|
|**totalCount**|Integer|会话总数|
### <div id="HostStatistic">HostStatistic</div>
|名称|类型|描述|
|---|---|---|
|**host**|String|会话源端IP|
|**activeCount**|Integer|活跃会话总数|
|**threadIdList**|String|会话id列表|
|**totalCount**|Integer|会话总数|
### <div id="UserStatistic">UserStatistic</div>
|名称|类型|描述|
|---|---|---|
|**user**|String|会话用户|
|**activeCount**|Integer|活跃会话总数|
|**threadIdList**|String|会话id列表|
|**totalCount**|Integer|会话总数|
### <div id="Session">Session</div>
|名称|类型|描述|
|---|---|---|
|**id**|Integer|会话id|
|**user**|String|会话用户|
|**host**|String|会话源端IP|
|**db**|String|数据库名|
|**cmd**|String|session命令|
|**active**|Boolean|当前活跃状态|
|**time**|Integer|会话建立时间|
|**state**|String|会话状态|
|**info**|String|正在执行的sql|
|**duration**|Integer|事务持续时间|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
