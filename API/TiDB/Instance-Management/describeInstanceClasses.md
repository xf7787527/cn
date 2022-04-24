# describeInstanceClasses


## 描述
规格获取接口

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances:describeInstanceClasses

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**storageType**|String|True| |存储类型,目前只支持本地SSD;|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeinstanceclasses#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**tidbFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
|**tikvFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
|**pdFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
|**monitorFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
|**tiflashFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
|**ticdcFlavors**|[NodeFlavor](describeinstanceclasses#nodeflavor)| |
### <div id="nodeflavor">NodeFlavor</div>
|名称|类型|描述|
|---|---|---|
|**maxNum**|Integer|允许的最大节点数|
|**minNum**|Integer|允许的最小节点数|
|**flavors**|[Flavor[]](describeinstanceclasses#flavor)| |
### <div id="flavor">Flavor</div>
|名称|类型|描述|
|---|---|---|
|**instanceClass**|String|规格代码,如tidb.s1.xlarge|
|**cpu**|Integer|cpu核数|
|**memoryGB**|Integer|内存大小，单位GB|
|**storageGB**|Integer[]|该规格支持的存储空间，单位GB|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
