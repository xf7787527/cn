# listDomains


## 描述
获取网站列表

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ListDomains](listdomains#listdomains)|True| |请求|
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
|**result**|[Result](listdomains#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**wafInstanceId**|String|实例id|
|**list**|String[]|网站列表|
|**pageIndex**|Integer|页码|
|**pageSize**|Integer|页大小|
|**totalCount**|Integer|该实例下总共的域名数量|
|**maxLimit**|Integer|最大支持的数目|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
