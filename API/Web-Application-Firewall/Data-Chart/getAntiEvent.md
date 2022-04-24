# getAntiEvent


## 描述
获取网站在一定时间内的报表详情。

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/chart:getAntiEvent

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[GetAntiEventReq](getantievent#getantieventreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="getantieventreq">GetAntiEventReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|False| |实例id，代表要查询的WAF实例，为空时表示当前用户下的所有实例|
|**domain**|String|False| |域名，为空时表示当前实例下的所有域名|
|**antiType**|String|True| |攻击类型，支持类型："cc"(cc攻击)，"waf"(Web攻击)，"acl"(自定义规则)|
|**remoteAddr**|String|False| |源ip，检索字段|
|**antiStatus**|String|False| |状态码，检索字段|
|**start**|Integer|True| |开始时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**end**|Integer|True| |结束时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**pageSize**|Integer|True| |每页显示的个数。|
|**pageIndex**|Integer|True| |页数。|
|**sortKey**|String|False| |排序字段，document_uri:uri, remote_addr:源ip, time:时间|
|**sortDesc**|String|False| |排序方式，desc-倒序 asc-增序|
|**isExport**|Boolean|False| |false表示查询，true表示导出|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getantievent#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageSize**|Integer|每页显示的个数。|
|**pageIndex**|Integer|页数。|
|**total**|Integer|总个数。|
|**events**|[AntiEvent[]](getantievent#antievent)|查询报表详情列表|
### <div id="antievent">AntiEvent</div>
|名称|类型|描述|
|---|---|---|
|**remoteAddr**|String|源ip|
|**csaInfo**|String|情报标签|
|**riskLevel**|String|风险等级|
|**area**|String|来源地区|
|**accessTime**|Integer|产生时间|
|**method**|String|方法|
|**attackType**|String|攻击类型|
|**url**|String|url|
|**payLoad**|String|恶意负载|
|**action**|String|动作|
|**ruleName**|String|规则名称|
|**logId**|String|日志Id|
|**isReported**|Integer|该信息是否已上报AI平台，0表示否|
|**wafInstanceId**|String|实例id|
|**antiStatus**|String|状态码|
|**upstreamErr**|String|状态标识|
|**skipExist**|Integer|是否已加入白名单，0表示否|
|**denyExist**|Integer|是否已加入黑名单，0表示否|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
