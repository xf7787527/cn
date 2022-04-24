# setWafCondition


## 描述
设置网站waf自定义防护条件

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:setCondition

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[SetWafConditionReq](setwafcondition#setwafconditionreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="setwafconditionreq">SetWafConditionReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|Integer|False| |0:新增，大于0:更新|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**conditionName**|String|False| |条件名称，新增时必须|
|**conditionType**|String|True| |匹配类型，"str"/"regex"/"geo"/"size"/"ip"/"SQLi"/"XSS"|
|**filters**|[FilterCfg[]](setwafcondition#filtercfg)|True| |过滤器配置|
### <div id="filtercfg">FilterCfg</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**id**|Integer|False| |序号,不作更新使用|
|**partOfReq**|String|False| |请求位置 当匹配类型为"str"/"regex"/"size"时，可选字段：["headers"/"cookie"/"args"/"body"/"uri"/"method"] | 匹配类型为"SQLi"/"XSS"时:可选字段：["headers"/"cookie"/"args"/"body"/"uri"]|当匹配类型为"geo"/"ip"时，该字段为空|
|**reqKey**|String|False| |指定key，匹配类型为"geo"/"ip"时，该字段为空,|  partOfReq为uri/body/method 时，该字段为空，header/cookie时非空，args时选填|
|**matchLogic**|String|False| |匹配类型"str"时：["startsWith"/"endsWith"/"contains"/"equal"]|匹配类型为"geo"/"SQLi"/"XSS"/"regex"时：""|匹配类型为"size"时：["equal"/"notEquals"/"greaterThan"/"greaterThanOrEqual"/"lessThan"/"lessThanOrEqual"]|
|**reqValue**|String|False| |// 匹配类型为"SQLi"/"XSS"时:""，匹配类型为"geo"时:该值为省份名称。匹配类型为"ip"时，该值为 ipv4/8/16/24/32)/ipv6/64 ipv6/128)| 匹配类型为"size"时:数字字符串 其他类型不限|
|**decodeFunc**|String|False| |仅type为str regex SQLi XSS时可非空，取值"","lowercase","trim","base64Decode","urlDecode","htmlDecode","hexDecode","sqlTrim"按先后顺序，多个时用 , 分隔|
|**isBase64Decode**|String|False| |不解码"base64Decode"解码,str时才有|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
