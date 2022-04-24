# getAvailableCertForDomain


## 描述
获取域名可用证书列表

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/cert:availableForDomain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[GetAvailableCertReq](getavailablecertfordomain#getavailablecertreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="getavailablecertreq">GetAvailableCertReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |实例id，代表要查询的WAF实例|
|**domain**|String|True| |域名|
|**isGm**|Integer|False| |是否国密|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getavailablecertfordomain#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bindCertId**|String|现绑定证书id|
|**bindCertName**|String|现绑定证书名称|
|**certIds**|String[]|域名可用证书id列表|
|**certNames**|String[]|域名可用证书名称列表|
|**count**|Integer|可用证书个数|
|**domain**|String|域名|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
