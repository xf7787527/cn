# describeNodeClasses


## 描述
查询 node 可用规格

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances:describeNodeClasses

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**nodeType**|String|False| |节点类型 CH ZK Monitor|
|**nodeStorageType**|String|False| |存储类型： EBS_SSD|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describenodeclasses#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**chSpec**|[ChSpec](describenodeclasses#chspec)| |
|**zkSpec**|[ZkSpec](describenodeclasses#zkspec)| |
|**monitorSpec**|[MonitorSpec](describenodeclasses#monitorspec)| |
<div id="monitorspec">MonitorSpec</div>
|名称|类型|描述|
|---|---|---|
|**flavors**|[Flavor[]](describenodeclasses#flavor)|规格代码|
<div id="flavor">Flavor</div>
|名称|类型|描述|
|---|---|---|
|**nodeClass**|String|规格代码|
|**cpu**|Integer|cup核数|
|**memoryGB**|Integer|内存大小|
|**storageGBRange**|String|该规格支持的存储空间的最小值，最大值及步长，用英文逗号分隔，例如100,4000,50 表示最小存储空间100GB，最大空间4000GB，步长50GBZK节点无须返回该字段|
<div id="zkspec">ZkSpec</div>
|名称|类型|描述|
|---|---|---|
|**flavors**|[Flavor[]](describenodeclasses#flavor)|规格代码|
|**minNum**|Integer|ZooKeeper节点的最小数目|
|**maxNum**|Integer|ZooKeeper节点的最大数目|
<div id="chspec">ChSpec</div>
|名称|类型|描述|
|---|---|---|
|**flavors**|[Flavor[]](describenodeclasses#flavor)|规格代码|
|**partitionMaxNum**|Integer|支持的最大分片数|
|**replicaMaxNum**|Integer|支持的最大副本数|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
