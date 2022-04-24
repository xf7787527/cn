# logout


## 描述
退出登录

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/instance:logout

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**error**|[Error](logout#error)| |

### <div id="error">Error</div>
|名称|类型|描述|
|---|---|---|
|**code**|Integer|0，成功；-1，失败。|
|**message**|String|错误消息。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
