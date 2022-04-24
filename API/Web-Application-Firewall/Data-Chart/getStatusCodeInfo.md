# getStatusCodeInfo


## 描述
获取网站在一定时间内的状态码报表信息。

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/chart:getStatusCodeInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[GetStatusCodeReq](getstatuscodeinfo#getstatuscodereq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="getstatuscodereq">GetStatusCodeReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|False| |实例id，代表要查询的WAF实例，为空时表示当前用户下的所有实例|
|**domain**|String|False| |域名，为空时表示当前实例下的所有域名|
|**start**|Integer|True| |开始时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**end**|Integer|True| |结束时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**statusCode**|String[]|False| |指定状态码，仅getStatusCodeInfo时有效|
|**isStaCode**|Boolean|False| |true表示获取状态码统计图、占比图。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getstatuscodeinfo#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**statusCodeData**|[StatusCodeData](getstatuscodeinfo#statuscodedata)|状态码TopN|
### <div id="statuscodedata">StatusCodeData</div>
|名称|类型|描述|
|---|---|---|
|**domainTop10**|[TopCodeValue[]](getstatuscodeinfo#topcodevalue)|异常状态码域名TOP10|
|**urlTop10**|[TopCodeValue[]](getstatuscodeinfo#topcodevalue)|异常状态码URL的TOP10|
|**statusCodeTotal**|[ChartItemValue](getstatuscodeinfo#chartitemvalue)|状态码响应统计，当请求字段isStaCode为true时返回|
|**statusCodePie**|[TopValue[]](getstatuscodeinfo#topvalue)|状态码响应占比，当请求字段isStaCode为true时返回|
### <div id="topvalue">TopValue</div>
|名称|类型|描述|
|---|---|---|
|**rank**|Integer|排名|
|**src**|String|具体值|
|**pv**|Integer|统计值|
### <div id="chartitemvalue">ChartItemValue</div>
|名称|类型|描述|
|---|---|---|
|**value**|Integer[]| |
### <div id="topcodevalue">TopCodeValue</div>
|名称|类型|描述|
|---|---|---|
|**rank**|Integer|排名|
|**src**|String|具体值|
|**pv**|Integer|统计值|
|**status_code**|[KVPair[]](getstatuscodeinfo#kvpair)| |
### <div id="kvpair">KVPair</div>
|名称|类型|描述|
|---|---|---|
|**key**|String| |
|**value**|Number| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
