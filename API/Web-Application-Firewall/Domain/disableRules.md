# disableRules


## 描述
规则开关

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:disableRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[DisableRulesReq](disablerules#disablerulesreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="disablerulesreq">DisableRulesReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |实例id，代表要设置的WAF实例|
|**domain**|String|True| |域名|
|**disable**|Integer|False| |0:使用规则，1：禁用规则|
|**ids**|Integer[]|False| |操作的规则id, ruleType非"waf"时必填|
|**ruleType**|String|True| |操作的规则类型，"waf":waf总体防护开关，"cc":cc规则，"ratelimit"：限速，"usrdefCookie":cookie类型的黑白名单，"usrdefGeo":geo类型的黑白名单，"usrdefHeaders":header类型的黑白名单，"usrdefIP":ip类型的黑白名单，"usrdefURI":uri类型的黑白名单，"filterReqresp":请求头类型的流量管理，"filterSenseinfo":敏感信息防泄漏，"usrdefWaf":waf自定义规则,"rewriteRule":重写规则（目前是uri重写规则）,"listRule":黑白名单规则（目前指method黑白名单）,"proxycache":url缓存，"botUsr":自定义类型BOT规则,"risk":风险防护规则,"riskEvent":风险控制事件,"riskUsrList":风险控制用户自定义名单|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](disablerules#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**wafInstanceId**|String|实例id|
|**list**|[DomainMainConfig[]](disablerules#domainmainconfig)|网站配置详情列表|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|该实例下总共的域名数量|
|**maxLimit**|Integer|最大支持的数目|
### <div id="domainmainconfig">DomainMainConfig</div>
|名称|类型|描述|
|---|---|---|
|**domain**|String|域名|
|**cname**|String|cname域名|
|**certName**|String|绑定的证书名称|
|**protocols**|String[]|使用协议，["http","https"]|
|**sslProtocols**|String[]|ssl协议，["TLSv1","TLSv1.1","TLSv1.2","SSLv2","SSLv3"]|
|**pureClient**|Integer|前置代理，1：使用 0：不使用|
|**httpStatus**|Integer|协议状态，0：正常|
|**httpsCertUpdateStatus**|Integer|https证书绑定状态|
|**gmHttpsCertUpdateStatus**|Integer|国密https证书绑定状态|
|**gmCertSupport**|Integer|是否支持国密证书|
|**antiStatus**|[AntiStatus](disablerules#antistatus)|防护状态，0：关闭 1：开启|
|**disableWaf**|Integer|1：bypass 0：防护模式|
|**attackInfo**|[AttackInfo](disablerules#attackinfo)|近七天攻击详情|
|**dnsStatus**|[DnsStatus](disablerules#dnsstatus)|网站dns配置|
|**enableCname2Rs**|Integer|cname解析状态。0为解析到VIP，1为解析到回源地址|
|**enableIpv6**|Integer|cname解析状态。0为解析到VIP，1为解析到回源地址|
|**region**|[DomainRegionInfo](disablerules#domainregioninfo)|域名的地域信息，类型是map[string]regionVipInfo|
### <div id="domainregioninfo">DomainRegionInfo</div>
|名称|类型|描述|
|---|---|---|
|**hb_bgp**|[RegionVipInfo](disablerules#regionvipinfo)|域名的在华北的vip和选中信息|
|**hd_bgp**|[RegionVipInfo](disablerules#regionvipinfo)|域名的在华东的vip和选中信息|
|**hn**|[RegionVipInfo](disablerules#regionvipinfo)|域名的在华南的vip和选中信息|
### <div id="regionvipinfo">RegionVipInfo</div>
|名称|类型|描述|
|---|---|---|
|**chosen**|Boolean|true-选中，false-未选中|
|**vips**|String[]|vip|
### <div id="dnsstatus">DnsStatus</div>
|名称|类型|描述|
|---|---|---|
|**statusCode**|Integer|接入状态。0表示既没有cname，也没有流量，1表示有cname接入，没有流量，2代表两者都有|
|**statusMsg**|String|接入状态描述|
### <div id="attackinfo">AttackInfo</div>
|名称|类型|描述|
|---|---|---|
|**aclAnti**|Long|自定义规则防护|
|**ccAnti**|Long|cc防护|
|**wafAnti**|Long|web防护|
### <div id="antistatus">AntiStatus</div>
|名称|类型|描述|
|---|---|---|
|**acl**|Integer|自定义规则|
|**cc**|Integer|cc防护|
|**waf**|Integer|waf防护|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
