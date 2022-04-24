# listWafConditions


## 描述
获取网站waf自定义防护条件

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:listConditions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListWafConditionsReq](listwafconditions#listwafconditionsreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="listwafconditionsreq">ListWafConditionsReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**pageIndex**|Integer|False| |页码，[1-100]，默认是1|
|**pageSize**|Integer|False| |页大小，[1-100]，默认是10|
|**conditionName**|String|False| |可选，筛选条件，对值不做校验|
|**conditionType**|String|False| |可选，筛选条件，模糊匹配|
|**id**|Integer|False| |可选，筛选条件|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](listwafconditions#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|配置总数|
|**list**|[ListWafConditionCfg](listwafconditions#listwafconditioncfg)|网站waf自定义防护条件配置|
### <div id="listwafconditioncfg">ListWafConditionCfg</div>
|名称|类型|描述|
|---|---|---|
|**conditionName**|String|名称|
|**conditionType**|String|匹配类型|
|**id**|Integer|序号|
|**ruleNames**|String[]|规则名称|
|**updateTime**|Integer|更新时间，s|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
