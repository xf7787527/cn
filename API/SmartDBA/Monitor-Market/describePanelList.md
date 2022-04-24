# describePanelList


## 描述
获取监控大盘列表

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/panels

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbType**|String|False| |数据库类型,默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describepanellist#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[Panel[]](describepanellist#panel)|列表|
### <div id="Panel">Panel</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|监控大盘名称|
|**panelGid**|String|监控大盘id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
