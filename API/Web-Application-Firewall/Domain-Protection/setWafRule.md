# setWafRule


## 描述
设置waf自定义规则

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:setRule

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[SetWafRuleReq](setwafrule#setwafrulereq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="setwafrulereq">SetWafRuleReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|Integer|True| |规则id,新增时传0|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**ruleName**|String|True| |规则名称|
|**matchAction**|String|True| |匹配动作, forbidden redirect verify@jscookie verify@captcha notice|
|**redirection**|String|True| |跳转地址，matchAction为redirect时必须为当前实例下的域名的url，forbidden时为自定义页面名称|
|**conditions**|[ConditionIdSet[]](setwafrule#conditionidset)|True| |条件集|
### <div id="conditionidset">ConditionIdSet</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**conditionId**|Integer|True| |条件Id|
|**opposite**|String|True| |对条件结果的取反操作，does不取反，doesnot取反|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
