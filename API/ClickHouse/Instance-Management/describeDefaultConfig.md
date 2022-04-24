# describeDefaultConfig


## 描述
查询 Clickhouse 推荐规格

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances:describeDefaultConfig

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chNodeClass**|String|False| |计算节点规格|
|**shardNum**|Integer|False| |分片数|
|**replicaNum**|Integer|False| |副本数|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describedefaultconfig#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**zkNodeClass**|String| |
|**zkNodeNum**|Integer| |
|**zkNodeCPU**|Integer| |
|**zkNodeMemoryGB**|Integer| |
|**zkNodeStorageGB**|Integer| |
|**monitorNodeClass**|String| |
|**monitorNodeCPU**|Integer| |
|**monitorNodeMemoryGB**|Integer| |
|**monitorNodeStorageGB**|Integer| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
