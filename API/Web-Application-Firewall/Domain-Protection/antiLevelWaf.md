# antiLevelWaf


## 描述
设置waf策略等级

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/waf:antiLevel

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[AntiLevelWafReq](antilevelwaf#antilevelwafreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="antilevelwafreq">AntiLevelWafReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|
|**wafLevel**|Integer|False| |0表示宽松，1表示正常，2表示严格, 3表示自定义|
|**usrPolicy**|Long|False| |自定义规则集id，wafLevel为3时可以设置|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
