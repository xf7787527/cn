# getDomainLbConfig


## 描述
获取网站lb配置

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:getDomainLbConfig

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[CommonReq](getdomainlbconfig#commonreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="commonreq">CommonReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getdomainlbconfig#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**wafInstanceId**|String|实例id|
|**config**|[LbConfig](getdomainlbconfig#lbconfig)|网站lb配置|
### <div id="lbconfig">LbConfig</div>
|名称|类型|描述|
|---|---|---|
|**domain**|String|域名|
|**lbConf**|[LbConf](getdomainlbconfig#lbconf)|网站lb配置|
### <div id="lbconf">LbConf</div>
|名称|类型|描述|
|---|---|---|
|**protocols**|String[]|使用协议，["http","https"]|
|**sslProtocols**|String[]|ssl协议，eg:["TLSv1","TLSv1.1","TLSv1.2","SSLv2","SSLv3","TLSv1.3"]|
|**lbType**|String|负载均衡算法，eg:"rr"，"ip_hash"|
|**rsConfig**|[RsConfig](getdomainlbconfig#rsconfig)|网站回源配置|
|**pureClient**|Integer|是否使用前置代理，0为未使用，1为使用|
|**httpsRedirect**|Integer|1为跳转 0为不跳转|
|**rsOnlySupportHttp**|Integer|用户服务器是否只能http回源，1为是，0为否|
|**httpsCertUpdateStatus**|Integer|https证书状态,非配置项。-10为未绑定，0为已绑定|
|**gmHttpsCertUpdateStatus**|Integer|国密https证书状态,非配置项。-10为未绑定，0为已绑定|
|**gmCertSupport**|Integer|是否支持国密证书|
|**httpStatus**|Integer|协议状态,非配置项。0为正常，-10为不正常|
|**httpVersion**|String|Waf侧支持http版本，""为默认值http1.1,"http2"为http2|
|**enableKeepalive**|Integer|回源是否支持长链接，0为否|
|**suiteLevel**|Integer|加密套件等级，0表示默认为中级，1表示高级，2表示低级, 3表示自定义|
|**userSuiteLevel**|String[]|自定义加密套件|
|**enableUnderscores**|Integer|请求头是否支持下划线，1-是，0-否|
|**maxBodySize**|String|请求body最大值，默认300M，可为G/K|
|**disableHealthCheck**|Integer|禁用被动健康检查，缺省为0-否|
|**proxyConnectTimeout**|Integer|连接超时时间，3-60s|
### <div id="rsconfig">RsConfig</div>
|名称|类型|描述|
|---|---|---|
|**rsAddr**|String[]|回源地址|
|**weight**|Integer[]|回源地址权重，与rsAddr顺序对应|
|**httpRsPort**|String[]|http回源端口|
|**httpsRsPort**|String[]|https回源端口|
|**rsType**|Integer|回源地址类型，0为ip，1为域名|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
