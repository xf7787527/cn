# listMainCfg


## 描述
获取网站

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:listMainCfg

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListDomains](listmaincfg#listdomains)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="listdomains">ListDomains</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|False| |域名|
|**pageIndex**|Integer|False| |页码，[1-100]，默认为1|
|**pageSize**|Integer|False| |页大小，[1-100]，默认为10|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](listmaincfg#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**wafInstanceId**|String|实例id|
|**list**|[DomainMainConfig[]](listmaincfg#domainmainconfig)|网站配置详情列表|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
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
|**antiStatus**|[AntiStatus](listmaincfg#antistatus)|防护状态，0：关闭 1：开启|
|**disableWaf**|Integer|1：bypass 0：防护模式|
|**attackInfo**|[AttackInfo](listmaincfg#attackinfo)|近七天攻击详情|
|**dnsStatus**|[DnsStatus](listmaincfg#dnsstatus)|网站dns配置|
|**enableCname2Rs**|Integer|cname解析状态。0为解析到VIP，1为解析到回源地址|
|**enableIpv6**|Integer|cname解析状态。0为解析到VIP，1为解析到回源地址|
|**region**|[DomainRegionInfo](listmaincfg#domainregioninfo)|域名的地域信息，类型是map[string]regionVipInfo|
### <div id="domainregioninfo">DomainRegionInfo</div>
|名称|类型|描述|
|---|---|---|
|**hb_bgp**|[RegionVipInfo](listmaincfg#regionvipinfo)|域名的在华北的vip和选中信息|
|**hd_bgp**|[RegionVipInfo](listmaincfg#regionvipinfo)|域名的在华东的vip和选中信息|
|**hn**|[RegionVipInfo](listmaincfg#regionvipinfo)|域名的在华南的vip和选中信息|
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
