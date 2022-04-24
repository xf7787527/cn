# enableCname2RsExternal


## 描述
cname解析到回源

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:enableCname2RsExternal

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[ActiveFuncReq](enablecname2rsexternal#activefuncreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="activefuncreq">ActiveFuncReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|False| |实例id，代表要设置的WAF实例|
|**domain**|String|True| |域名|
|**enable**|Integer|False| |是否使能 0表示否|
|**isGm**|Integer|False| |是否国密|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
