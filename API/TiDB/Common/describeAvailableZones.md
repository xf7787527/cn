# describeAvailableZones


## 描述
获取可用区

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/azs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeavailablezones#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**availableZones**|String[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
