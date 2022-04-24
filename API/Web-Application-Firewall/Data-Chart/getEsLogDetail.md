# getEsLogDetail


## 描述
获取网站在一定时间内的日志详情。

## 请求方式
GET

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/chart:getEsLog

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|False| |实例id，代表要查询的WAF实例，为空时表示当前用户下的所有实例|
|**domain**|String|False| |域名，为空时表示当前实例下的所有域名|
|**remote_addr**|String|False| |来源ip，检索字段|
|**document_uri**|String|False| |URI，检索字段|
|**url**|String|False| |url，检索字段|
|**anti_geo**|String|False| |来源地域，检索字段|
|**request_method**|String|False| |请求方法，检索字段|
|**action**|String|False| |动作，检索字段，支持类型：""(为空时，默认查询全部动作类型)，"-"(放行)，"notice"(观察)，"forbidden OR status"(拦截)，"redirect"(浏览器跳转)，"verify"(人机交互)|
|**status**|String|False| |状态码，检索字段|
|**logType**|String[]|False| |日志类型，检索字段，支持类型：""(为空时，默认查询全部日志类型)，"access"(访问日志)，"waf"(wafSDK)，"acl"(自定义规则)，"skip"(白名单)，"deny"(黑名单)，"cc"(CC攻击)，"webcache"(网页防篡改)，"css"(跨站脚本攻击)，"sqli"(SQL注入攻击)，""fileinc"(文件读取/包含攻击)，"cmding"(命令/代码执行攻击)，"sdd"(敏感文件探测)，"malscan"(恶意扫描攻击)，"bckack"(恶意/后门文件攻击)，"xmli"(XML注入攻击)，"dirt"(目录遍历攻击)|
|**logId**|String|False| |日志Id，检索字段|
|**start**|Integer|True| |开始时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**end**|Integer|True| |结束时间戳，单位秒，时间间隔要求大于5分钟，小于30天。|
|**pageSize**|Integer|True| |每页显示的个数，默认是10。|
|**pageIndex**|Integer|True| |页数，默认是1。|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](geteslogdetail#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageSize**|Integer|每页显示的个数。|
|**pageIndex**|Integer|页数。|
|**total**|Integer|总个数。|
|**events**|[EsLogEvent[]](geteslogdetail#eslogevent)|查询日志详情列表|
### <div id="eslogevent">EsLogEvent</div>
|名称|类型|描述|
|---|---|---|
|**accessTime**|Integer|产生时间|
|**remoteAddr**|String|源ip|
|**remotePort**|String|客户端port|
|**domain**|String|域名|
|**area**|String|来源地区|
|**method**|String|方法|
|**url**|String|url|
|**payLoad**|String|恶意负载|
|**status**|String|响应信息|
|**logType**|String|日志类型|
|**action**|String|动作|
|**requestId**|String|请求ID|
|**upstreamErr**|String|回源错误信息|
|**timeLocal**|String|日志记录时间|
|**hostname**|String|本机域名|
|**bytesSent**|String|响应长度|
|**requestLength**|String|请求长度|
|**host**|String|客户端请求的域名|
|**serverAddr**|String|jfe的server块监听IP|
|**serverPort**|String|jfe的server块监听port|
|**upstreamHttpName**|String|请求所连接的upstream名称|
|**upstreamAddr**|String|请求所连接的upstream服务器IP|
|**upstreamHttpPort**|String|请求所连接的upstream服务器port|
|**upstreamConnectTime**|String|等待upstream建立连接的时间|
|**upstreamHeaderTime**|String|接收upstream请求头的时间|
|**upstreamResponseTime**|String|接收upstream响应头的时间|
|**requestTime**|String|请求处理时间|
|**httpUserAgent**|String|请求头的UA字段|
|**antiReason**|String|攻击类型|
|**httpReferer**|String|请求来源|
|**scheme**|String|请求协议|
|**uri**|String|uri|
|**sentHttpContentRange**|String|断点续传响应分片位置|
|**antiRemoteAddr**|String|客户端IP|
|**antiStatus**|String|原响应码|
|**antiReqRaw**|String|命中规则请求原始请求报文|
|**antiRespRaw**|String|命中规则请求原始响应报文|
|**antiGeo**|String|来源地域信息|
|**antiRiskFid**|String|指纹ID|
|**antiRiskRaw**|String|指纹采集详细信息|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
