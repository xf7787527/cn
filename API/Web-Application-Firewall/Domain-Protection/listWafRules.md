# listWafRules


## 描述
获取网站的waf自定义规则

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:listRules

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListRulesReq](listwafrules#listrulesreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="listrulesreq">ListRulesReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**ruleType**|String|False| |规则类型|
|**pageIndex**|Integer|False| |页码，[1-100]，默认是1|
|**pageSize**|Integer|False| |页大小，[1-100]，默认是10|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](listwafrules#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|配置总数|
|**data**|[ListWafRuleCfg](listwafrules#listwafrulecfg)|网站waf自定义规则|
### <div id="listwafrulecfg">ListWafRuleCfg</div>
|名称|类型|描述|
|---|---|---|
|**conditions**|[ConditionNameSet[]](listwafrules#conditionnameset)|使用的条件集|
|**id**|Integer|规则id|
|**matchAction**|String|匹配动作|
|**redirection**|String|重定向连接|
|**ruleName**|String|规则名称|
|**updateTime**|Integer|规则更新时间|
|**disable**|Integer|0-使用中，1-禁用|
### <div id="conditionnameset">ConditionNameSet</div>
|名称|类型|描述|
|---|---|---|
|**conditionName**|String|条件名称|
|**opposite**|String|对条件结果的取反操作，does不取反，doesnot取反|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
