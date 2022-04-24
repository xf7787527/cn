# getPanelRelateClusters


## 描述
获取关联实例

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/panels/{panelGid}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**panelGid**|String|True| |监控大盘id|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbType**|String|False| |数据库类型,默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getpanelrelateclusters#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[PanelClusterItem[]](getpanelrelateclusters#panelclusteritem)|列表|
### <div id="PanelClusterItem">PanelClusterItem</div>
|名称|类型|描述|
|---|---|---|
|**instanceName**|String|rds实例名称|
|**instanceId**|String|rds实例id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
