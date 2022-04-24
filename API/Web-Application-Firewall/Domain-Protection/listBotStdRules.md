# listBotStdRules


## 描述
获取网站已知类型bot规则

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/bot:listStdRule

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListBotStdRuleReq](listbotstdrules#listbotstdrulereq)|True| |请求|
|**userPin**|String|True| |用户pin|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="listbotstdrulereq">ListBotStdRuleReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |域名|
|**botType**|String|False| |bot类型，模糊检索|
|**pageSize**|Integer|False| |页面大小，默认10|
|**pageIndex**|Integer|False| |页码，默认1|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](listbotstdrules#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|配置总数|
|**list**|[StdBotRules](listbotstdrules#stdbotrules)|已知类型bot规则|
### <div id="stdbotrules">StdBotRules</div>
|名称|类型|描述|
|---|---|---|
|**botType**|String|bot类型|
|**subType**|String[]|bot子类|
|**disable**|Integer|0-使用中，1-禁用|
|**action**|[DenyActionCfg](listbotstdrules#denyactioncfg)|动作配置|
### <div id="denyactioncfg">DenyActionCfg</div>
|名称|类型|描述|
|---|---|---|
|**atOp**|Integer|黑名单匹配动作类型 1-4 分别表示forbidden@1 redirect@2 verify@captcha3 verify@jscookie4 5-告警(自定义bot增加)，6-302cookie(自定义bot增加), 7-cc动态防护|
|**atVal**|String|黑名单匹配动作内容 当atOp为3/4/7时，atVal为空，atOp=1时，atVal为自定义页面,atOp=2时，atVal为跳转url。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
