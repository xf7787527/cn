# modifyNodeNum


## 描述
增加实例的节点数量。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyNodeNum

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tidbNodeNum**|Integer|False| |调整后的tidb节点数|
|**tikvNodeNum**|Integer|False| |调整后的tikv节点数|
|**pdNodeNum**|Integer|False| |调整后的pd节点数|
|**tiflashNodeSpec**|[NodeSpec](modifynodenum#nodespec)|False| |TiFlash节点规格和数目|
|**ticdcNodeSpec**|[NodeSpec](modifynodenum#nodespec)|False| |Ticdc节点规格和数目|

### <div id="nodespec">NodeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**nodeType**|String|True| |节点类型：tidb、tikv、pd、monitor|
|**nodeNum**|Integer|True| |节点数|
|**nodeClass**|String|True| |节点的规格代码|
|**cpu**|Integer|False| |cpu核数|
|**memoryGB**|Integer|False| |内存大小，单位GB|
|**storageType**|String|True| |存储类型|
|**storageGB**|Integer|True| |存储空间，单位GB|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](modifynodenum#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**orderId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
