# updatePanelClusters


## 描述
修改关联实例，每次都是全量下发

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/panels/{panelGid}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**panelGid**|String|True| |监控大盘id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceIdList**|String[]|False| | |
|**dbType**|String|False| |数据库类型,默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
