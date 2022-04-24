# describeLbOutIp


## 描述
获取回源ip段

## 请求方式
GET

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/admin:lboutIp

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| | |

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describelboutip#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**list**|Map| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
