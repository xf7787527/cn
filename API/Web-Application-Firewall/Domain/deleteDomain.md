# deleteDomain


## 描述
删除网站

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/wafInstanceIds/{wafInstanceId}/domain:delete

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**wafInstanceId**|String|True| |实例Id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[CommonReq](deletedomain#commonreq)|True| |请求|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="commonreq">CommonReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**wafInstanceId**|String|True| |WAF实例id|
|**domain**|String|True| |域名|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
