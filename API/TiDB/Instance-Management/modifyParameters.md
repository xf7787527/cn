# modifyParameters


## 描述
修改TiDB实例的配置参数。部分参数修改后，需要重启才能生效，具体可以参考PingCAP的相关文档

## 请求方式
PUT

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/parameters

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parameters**|[ModifyParam[]](modifyparameters#modifyparam)|True| | |

### <div id="modifyparam">ModifyParam</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |参数名称|
|**value**|String|False| |参数修改值|
|**nodeType**|String|False| |参数的节点类型，包括TiKV,TiDB,PD,TiFlash|

## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
