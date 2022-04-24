# getDomainAntiConfig


## 描述
获取域名防护配置

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:getAntiConfig

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[CommonReq](getdomainanticonfig#commonreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="commonreq">CommonReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getdomainanticonfig#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**domain**|String|域名|
|**disableWaf**|Integer|waf状态 1表示关闭waf|
|**aclConf**|[AclConf](getdomainanticonfig#aclconf)|网站waf防护配置|
|**antispiderConf**|[EnableConf](getdomainanticonfig#enableconf)|网站防爬虫防护配置|
|**ccConf**|[CcConf](getdomainanticonfig#ccconf)|网站cc防护配置|
|**denyConf**|[DenyConf](getdomainanticonfig#denyconf)|网站黑名单防护配置|
|**intSemConf**|[IntSemConf](getdomainanticonfig#intsemconf)|网站智能语义引擎防护配置|
|**ipbanConf**|[IpbanConf](getdomainanticonfig#ipbanconf)|网站恶意ip防护配置|
|**ratelimitConf**|[RatelimitConf](getdomainanticonfig#ratelimitconf)|网站限速规则防护配置|
|**threatinfoConf**|[EnableConf](getdomainanticonfig#enableconf)|网站威胁情报防护配置|
|**userDefPageConf**|[UserDefPageConf](getdomainanticonfig#userdefpageconf)|网站自定义页面配置|
|**wafConf**|[WafConf](getdomainanticonfig#wafconf)|网站waf防护配置|
|**webUserdefConf**|[WebUserdefConf](getdomainanticonfig#webuserdefconf)|网站web自定义规则防护配置|
|**webcacheConf**|[EnableConf](getdomainanticonfig#enableconf)|网站防篡改防护配置|
|**skipConf**|[SkipConf](getdomainanticonfig#skipconf)|网站白名单防护配置|
|**filterHeaderConf**|[FilterHeaderConf](getdomainanticonfig#filterheaderconf)|网站请求头管理防护配置|
|**filterSenseConf**|[FilterSenseConf](getdomainanticonfig#filtersenseconf)|网站敏感信息防护配置|
|**statusConf**|[StatusConf](getdomainanticonfig#statusconf)|状态码修改配置|
|**uriRewriteConf**|[UriRewriteConf](getdomainanticonfig#urirewriteconf)|网站uri重写规则配置|
|**proxycacheConf**|[EnableConf](getdomainanticonfig#enableconf)|proxy缓存配置|
|**riskConf**|[RiskConf](getdomainanticonfig#riskconf)|risk配置|
|**botConf**|[BotConf](getdomainanticonfig#botconf)|bot配置|
### <div id="botconf">BotConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|已知类型bot。1-使能 0-禁止|
|**enableUserDefine**|Integer|自定义类型bot。1-使能 0-禁止|
|**enableThreatIp**|Integer|bot IDC开关。1-使能 0-禁止|
### <div id="riskconf">RiskConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|数据风控。1-使能 0-禁止|
|**enableAccount**|Integer|账户安全。1-使能 0-禁止|
### <div id="enableconf">EnableConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
### <div id="urirewriteconf">UriRewriteConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**uriRewriteNum**|Integer|uri重写规则条数|
### <div id="statusconf">StatusConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**statusNum**|Integer|响应码条数|
### <div id="filtersenseconf">FilterSenseConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**respCodeNum**|Integer|响应码条数  即将废弃|
|**senseinfoNum**|Integer|敏感信息条数|
|**total**|Integer|总条数|
### <div id="filterheaderconf">FilterHeaderConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**reqEnable**|Integer|是否使能请求头 0表示否|
|**respEnable**|Integer|是否使能响应头 0表示否|
|**reqHeaderNum**|Integer|请求头条数|
|**respHeaderNum**|Integer|响应头条数|
|**total**|Integer|总条数|
### <div id="skipconf">SkipConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**listNum**|Integer|规则条数|
### <div id="webuserdefconf">WebUserdefConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**conditionNum**|Integer|条件条数|
|**ruleNum**|Integer|规则条数|
### <div id="wafconf">WafConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**wafMode**|Integer|0表示防护，1表示预警|
|**wafLevel**|Integer|0表示宽松，1表示正常，2表示严格, 3表示自定义|
|**usrPolicy**|Long|自定义规则集Id|
|**redirection**|String|自定义页面名称|
### <div id="userdefpageconf">UserDefPageConf</div>
|名称|类型|描述|
|---|---|---|
|**pageNum**|Integer|条数|
### <div id="ratelimitconf">RatelimitConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**rateLimitNum**|Integer|条数|
### <div id="ipbanconf">IpbanConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**banTime**|Integer|封禁时间，秒|
|**detectTime**|Integer|检测时间，秒|
|**threshold**|Integer|封禁阈值|
### <div id="intsemconf">IntSemConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**mode**|String|模式|
### <div id="denyconf">DenyConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**listNum**|Integer|规则条数|
### <div id="ccconf">CcConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**ccMode**|Integer|0表示正常，1表示攻击紧急|
|**qps**|Integer|qps配置|
|**enableUserDefine**|Integer|是否支持自定义cc，0表示否|
|**rulesCount**|Integer|cc自定义规则个数|
|**action**|[DenyActionCfg](getdomainanticonfig#denyactioncfg)|动作配置，默认为告警，支持1，2，3和5四种类型动作|
### <div id="denyactioncfg">DenyActionCfg</div>
|名称|类型|描述|
|---|---|---|
|**atOp**|Integer|黑名单匹配动作类型 1-4 分别表示forbidden@1 redirect@2 verify@captcha3 verify@jscookie4 5-告警(自定义bot增加)，6-302cookie(自定义bot增加), 7-cc动态防护|
|**atVal**|String|黑名单匹配动作内容 当atOp为3/4/7时，atVal为空，atOp=1时，atVal为自定义页面,atOp=2时，atVal为跳转url。|
### <div id="aclconf">AclConf</div>
|名称|类型|描述|
|---|---|---|
|**enable**|Integer|是否使能 0表示否|
|**aclRuleNum**|Integer|acl规则个数|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
