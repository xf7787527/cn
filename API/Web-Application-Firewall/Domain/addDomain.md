# addDomain


## 描述
新增网站

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:add

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[AddDomain](adddomain#adddomain)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="adddomain">AddDomain</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |实例id，代表要设置的WAF实例|
|**domain**|String|True| |域名，单个|
|**domains**|String[]|False| |域名数组|
|**protocols**|String[]|True| |使用协议，eg:["http","https"]|
|**sslProtocols**|String[]|False| |ssl协议，eg:["TLSv1","TLSv1.1","TLSv1.2","SSLv2","SSLv3","TLSv1.3"]|
|**lbType**|String|True| |负载均衡算法，eg:"rr"，"ip_hash","weight_rr"|
|**rsConfig**|[RsConfig](adddomain#rsconfig)|True| |回源配置|
|**pureClient**|Integer|False| |是否使用前置代理，0为未使用，1为使用|
|**httpsRedirect**|Integer|False| |1为跳转 0为不跳转|
|**rsOnlySupportHttp**|Integer|False| |用户服务器是否只能http回源，1为是，0为否|
|**gmCertSupport**|Integer|False| |是否支持国密证书|
|**httpVersion**|String|False| |Waf侧支持http版本，不传时默认值为http1.1,传"http2"为http2|
|**enableKeepalive**|Integer|False| |回源是否支持长链接，0为否|
|**suiteLevel**|Integer|False| |加密套件等级，0表示默认为中级，1表示高级，2表示低级, 3表示自定义|
|**userSuiteLevel**|String[]|False| |自定义加密套件|
|**enableUnderscores**|Integer|False| |请求头是否支持下划线，0-否，1-是。缺省为0|
|**disableHealthCheck**|Integer|False| |禁用被动健康检查，缺省为0-否|
|**proxyConnectTimeout**|Integer|False| |连接超时时间，3-60s|
### <div id="rsconfig">RsConfig</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**rsAddr**|String[]|True| |回源地址|
|**weight**|Integer[]|False| |回源地址权重，与rsAddr顺序对应|
|**httpRsPort**|String[]|False| |http回源端口|
|**httpsRsPort**|String[]|False| |https回源端口|
|**rsType**|Integer|False| |回源地址类型，0为ip，1为域名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
