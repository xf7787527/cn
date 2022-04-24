# getQpsData


## 描述
获取网站在一定时间内的qps信息。

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/chart:getQpsData

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[GetChartReq](getqpsdata#getchartreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="getchartreq">GetChartReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|False| |实例id，代表要查询的WAF实例，为空时表示当前用户下的所有实例|
|**domain**|String|False| |域名，为空时表示当前实例下的所有域名|
|**start**|Integer|True| |开始时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**end**|Integer|True| |结束时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**isSum**|Boolean|False| |true表示和值图，false表示均值图，仅getBpsData， getQpsData时有效。|
|**isWafRule**|Boolean|False| |true表示查找命中不同规则的waf攻击对应数目。|
|**isRs**|Boolean|False| |true表示源站返回给waf的异常响应，false表示waf返回给客户端的异常响应，仅getExceptionData时有效。|
|**pieItem**|String|False| |ua表示返回ua的饼图数据，仅getPieChart时有效。|
|**statusCode**|String[]|False| |指定状态码，仅getStatusCodeInfo时有效|
|**isStaCode**|Boolean|False| |true表示获取状态码统计图、占比图。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getqpsdata#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**timeScope**|Long[]|时间戳，单位毫秒|
|**qps**|[Qps](getqpsdata#qps)|qps数据|
### <div id="qps">Qps</div>
|名称|类型|描述|
|---|---|---|
|**qpsTotal**|[ChartItemValue](getqpsdata#chartitemvalue)|qps统计数据|
|**wafAnti**|[ChartItemValue](getqpsdata#chartitemvalue)|waf防护统计数据|
|**ccAnti**|[ChartItemValue](getqpsdata#chartitemvalue)|cc防护统计数据|
|**aclAnti**|[ChartItemValue](getqpsdata#chartitemvalue)|精准访问控制防护统计数据|
|**cacheTotal**|[ChartItemValue](getqpsdata#chartitemvalue)|网站合规异常统计数据|
### <div id="chartitemvalue">ChartItemValue</div>
|名称|类型|描述|
|---|---|---|
|**value**|Integer[]| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
