# enableWafUserDefine


## 描述
激活waf自定义规则

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:setWafUserDefine

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[SetWafUserDefineReq](enablewafuserdefine#setwafuserdefinereq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="setwafuserdefinereq">SetWafUserDefineReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**enableUserDef**|Integer|False| |0禁止，1表示激活，默认为0|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
