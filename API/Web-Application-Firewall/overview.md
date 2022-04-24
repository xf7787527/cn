# 京东云WAF-OpenAPI接口


## 简介
京东云WAF-OpenAPI接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addDomain**|POST|新增网站|
|**antiLevelWaf**|POST|设置waf策略等级|
|**antiModeWaf**|POST|设置waf防护模式|
|**bindCert**|POST|绑定证书|
|**createInstance**|POST|创建waf实例|
|**delWafCondition**|POST|删除网站waf自定义防护条件|
|**delWafRule**|POST|删除waf自定义规则|
|**deleteDomain**|POST|删除网站|
|**describeLbOutIp**|GET|获取回源ip段|
|**disableRules**|POST|规则开关|
|**enableCname2RsExternal**|POST|cname解析到回源|
|**enableWaf**|POST|激活waf|
|**enableWafUserDefine**|POST|激活waf自定义规则|
|**getAntiEvent**|POST|获取网站在一定时间内的报表详情。|
|**getAvailableCertForDomain**|POST|获取域名可用证书列表|
|**getBpsData**|POST|获取网站在一定时间内的bps信息。|
|**getDomainAntiConfig**|POST|获取域名防护配置|
|**getDomainLbConfig**|POST|获取网站lb配置|
|**getEsLogDetail**|GET|获取网站在一定时间内的日志详情。|
|**getMainAntiInfoNew**|POST|获取网站在一定时间内主要的防护信息,新接口，无url响应时间分布。|
|**getQpsData**|POST|获取网站在一定时间内的qps信息。|
|**getStatusCodeInfo**|POST|获取网站在一定时间内的状态码报表信息。|
|**getWafInstance**|GET|获取实例ID及相关信息列表|
|**listBotStdRules**|POST|获取网站已知类型bot规则|
|**listDomains**|POST|获取网站列表|
|**listMainCfg**|POST|获取网站|
|**listWafConditions**|POST|获取网站waf自定义防护条件|
|**listWafFilter**|POST|获取网站waf自定义防护过滤器|
|**listWafRules**|POST|获取网站的waf自定义规则|
|**setWafCondition**|POST|设置网站waf自定义防护条件|
|**setWafRule**|POST|设置waf自定义规则|
|**updateDomain**|POST|更新网站|
|**upgradeInstance**|POST|升配订单|
