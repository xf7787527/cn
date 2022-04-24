# listWafFilter


## 描述
获取网站waf自定义防护过滤器

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:listFilter

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListWafFilterReq](listwaffilter#listwaffilterreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="listwaffilterreq">ListWafFilterReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**pageIndex**|Integer|False| |页码，[1-100]，默认是1|
|**pageSize**|Integer|False| |页大小，[1-100]，默认是10|
|**conditionId**|Integer|True| |筛选条件，所属条件的id|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](listwaffilter#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|配置总数|
|**list**|[ListWafFilterCfg](listwaffilter#listwaffiltercfg)|网站waf自定义防护过滤器设置|
### <div id="listwaffiltercfg">ListWafFilterCfg</div>
|名称|类型|描述|
|---|---|---|
|**wafInstanceId**|String|WAF实例id|
|**domain**|String|域名|
|**conditionId**|String|所属条件的id|
|**conditionName**|String|名称|
|**conditionType**|String|匹配类型|
|**filters**|[FilterCfg[]](listwaffilter#filtercfg)|过滤器配置|
### <div id="filtercfg">FilterCfg</div>
|名称|类型|描述|
|---|---|---|
|**id**|Integer|序号,不作更新使用|
|**partOfReq**|String|请求位置 当匹配类型为"str"/"regex"/"size"时，可选字段：["headers"/"cookie"/"args"/"body"/"uri"/"method"] | 匹配类型为"SQLi"/"XSS"时:可选字段：["headers"/"cookie"/"args"/"body"/"uri"]|当匹配类型为"geo"/"ip"时，该字段为空|
|**reqKey**|String|指定key，匹配类型为"geo"/"ip"时，该字段为空,|  partOfReq为uri/body/method 时，该字段为空，header/cookie时非空，args时选填|
|**matchLogic**|String|匹配类型"str"时：["startsWith"/"endsWith"/"contains"/"equal"]|匹配类型为"geo"/"SQLi"/"XSS"/"regex"时：""|匹配类型为"size"时：["equal"/"notEquals"/"greaterThan"/"greaterThanOrEqual"/"lessThan"/"lessThanOrEqual"]|
|**reqValue**|String|// 匹配类型为"SQLi"/"XSS"时:""，匹配类型为"geo"时:该值为省份名称。匹配类型为"ip"时，该值为 ipv4/8/16/24/32)/ipv6/64 ipv6/128)| 匹配类型为"size"时:数字字符串 其他类型不限|
|**decodeFunc**|String|仅type为str regex SQLi XSS时可非空，取值"","lowercase","trim","base64Decode","urlDecode","htmlDecode","hexDecode","sqlTrim"按先后顺序，多个时用 , 分隔|
|**isBase64Decode**|String|不解码"base64Decode"解码,str时才有|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
